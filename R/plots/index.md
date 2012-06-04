


..article: fill

<h1>
  <span class = 'yellow'>How to Do it with R</font><br/>
  <span class = 'white' style = 'font-size: 0.7em;'>
    A Tutorial
  </span><br/>
  <span class = 'white' style = 'font-size: 0.5em;'>
    by Ramnath Vaidyanathan
  </span>
</h1>

![slides](http://goo.gl/EpXln)

---

### Overview ###

The objective of this tutorial is to give you a quick overview of how to analyze data with `R`. We will focus our attention on the following topics

1. Data
2. Subset
3. Histogram
4. Boxplot
5. Scatterplot

---

### Data ###


We will work with the built-in data set `mtcars`.

<div class="chunk"><div class="rcode"><div class="output"><pre class="knitr">##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
</pre></div></div></div>


You can inspect the data set in many ways. 

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">View</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>       <span class="comment"># view data in rstudio</span>
<span class="functioncall">head</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>       <span class="comment"># view first six rows</span>
<span class="functioncall">head</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="number">10</span><span class="keyword">)</span>   <span class="comment"># view first ten rows</span>
<span class="functioncall">tail</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="number">20</span><span class="keyword">)</span>   <span class="comment"># view last twenty rows</span>
<span class="functioncall">NROW</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>       <span class="comment"># view number of rows </span>
<span class="functioncall">NCOL</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>       <span class="comment"># view number of columns</span>
<span class="functioncall">dim</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>        <span class="comment"># view rows x columns</span>
<span class="functioncall">str</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">)</span>        <span class="comment"># view structure of data</span>
</pre></div></div></div>


---

### Working with Subsets of Data ###

Very often you might want to work with a smaller subset of the data. `R` makes it very easy to select subsets by combining conditional operations. The main operations are

    == : equal to
    != : not equal to
    >= : greater or equal to
    <= : lesser or equal to
    &  : and
    |  : or
    
Below, you will find these operators applied to choose specific subsets of the `mtcars` data set.

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">subset</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="symbol">gear</span> == <span class="number">4</span><span class="keyword">)</span>           <span class="comment"># four gears</span>
<span class="functioncall">subset</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="symbol">cyl</span> <span class="keyword">!=</span> <span class="number">2</span><span class="keyword">)</span>            <span class="comment"># not 2 cylinders</span>
<span class="functioncall">subset</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="symbol">mpg</span> <span class="keyword">&gt;</span> <span class="number">20</span><span class="keyword">)</span>            <span class="comment"># mpg more than 20</span>
<span class="functioncall">subset</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="symbol">mpg</span> <span class="keyword">&gt;</span> <span class="number">20</span> <span class="keyword">&amp;</span> <span class="symbol">wt</span> <span class="keyword">&lt;</span> <span class="number">20</span><span class="keyword">)</span>  <span class="comment"># mpg &gt; 20 AND wt &lt; 20</span>
<span class="functioncall">subset</span><span class="keyword">(</span><span class="symbol">mtcars</span><span class="keyword">,</span> <span class="symbol">mpg</span> <span class="keyword">&gt;</span> <span class="number">20</span> <span class="keyword">|</span> <span class="symbol">wt</span> <span class="keyword">&lt;</span> <span class="number">20</span><span class="keyword">)</span>  <span class="comment"># mpg &gt; 20 OR wt &lt; 20</span>
</pre></div></div></div>


---

# Plotting with R #

---

### Basics ###

You will need to install the package `lattice` before you can start using it.

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">install.packages</span><span class="keyword">(</span><span class="string">'lattice'</span><span class="keyword">)</span>
</pre></div></div></div>


Once installed, you need to load the `lattice` package before you start plotting.

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">require</span><span class="keyword">(</span><span class="symbol">lattice</span><span class="keyword">)</span>
</pre></div></div></div>


If you are interested in economist style of plots, then you need to install the package `latticeExtra` and run the following commands before you start plotting

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">install.packages</span><span class="keyword">(</span><span class="string">'latticeExtra'</span><span class="keyword">)</span>
<span class="functioncall">require</span><span class="keyword">(</span><span class="symbol">latticeExtra</span><span class="keyword">)</span>
<span class="functioncall">trellis.theme.set</span><span class="keyword">(</span><span class="argument">theme</span> <span class="argument">=</span> <span class="functioncall">theEconomist.theme</span><span class="keyword">(</span><span class="argument">box</span> <span class="argument">=</span> <span class="string">'transparent'</span><span class="keyword">)</span><span class="keyword">)</span>
<span class="functioncall">lattice.options</span><span class="keyword">(</span><span class="functioncall">theEconomist.opts</span><span class="keyword">(</span><span class="keyword">)</span><span class="keyword">)</span>
</pre></div></div></div>


---

# Histograms #

---

### Basic Histogram ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/simple.svg" class="plot" /></div></div>


---

### Control Number of Bins ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">nint</span> <span class="argument">=</span> <span class="number">20</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/nint.svg" class="plot" /></div></div>


---

### Change Color ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'darkred'</span><span class="keyword">)</span> <span class="comment"># see colors() for more</span>
</pre></div></div><div class="rimage center"><img src="figure/col.svg" class="plot" /></div></div>


---

### Add x-Axis and y-Axis Labels ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">xlab</span> <span class="argument">=</span> <span class="string">'Miles per Gallon'</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/labels.svg" class="plot" /></div></div>


---

### Split by Single Categorical Variable ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span> <span class="keyword">|</span> <span class="symbol">cyl</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/single-cat.svg" class="plot" /></div></div>


---

### Split by Two Categorical Variables ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span> <span class="keyword">|</span> <span class="symbol">cyl</span> <span class="keyword">+</span> <span class="symbol">gear</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/two-cat.svg" class="plot" /></div></div>


---

### Histogram for a Subset of the Data ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">histogram</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">subset</span> <span class="argument">=</span> <span class="keyword">(</span><span class="symbol">gear</span> == <span class="number">4</span><span class="keyword">)</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/hist-sub.svg" class="plot" /></div></div>


---

### Histograms: Summary ###

Here is a short summary of the commands you have seen on histograms.

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>                       <span class="comment"># histogram of mpg</span>
<span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">nint</span> <span class="argument">=</span> <span class="number">20</span><span class="keyword">)</span>            <span class="comment"># 20 bins</span>
<span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'darkred'</span><span class="keyword">)</span>      <span class="comment"># colored darkred.</span>
<span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span> <span class="keyword">|</span> <span class="symbol">cyl</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>                 <span class="comment"># split by cyl</span>
<span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span> <span class="keyword">|</span> <span class="symbol">cyl</span> <span class="keyword">+</span> <span class="symbol">gear</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>          <span class="comment"># split by cyl and gear</span>
<span class="functioncall">hist</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">subset</span> <span class="argument">=</span> <span class="keyword">(</span><span class="symbol">gear</span> == <span class="number">4</span><span class="keyword">)</span><span class="keyword">)</span> <span class="comment"># specific subset</span>
</pre></div></div></div>


---

# Box and Whisker Plots #


---

### Simple Boxplot ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">bwplot</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/bwplot.svg" class="plot" /></div></div>


---

### Split by Single Categorical Variable ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">bwplot</span><span class="keyword">(</span><span class="keyword">~</span> <span class="symbol">mpg</span> <span class="keyword">|</span> <span class="symbol">cyl</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/bwplot1.svg" class="plot" /></div></div>


---

### Side by Side Boxplot ###

The boxplots drawn by `bwplot` are horizontal by default. Hence the `y` axis displays the categorical explanatory variable, while the `x` axis displays the numerical response variable

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">bwplot</span><span class="keyword">(</span><span class="symbol">cyl</span> <span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/bwplot2.svg" class="plot" /></div></div>


---

### Boxplot for a Subset of the Data ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">bwplot</span><span class="keyword">(</span><span class="symbol">cyl</span> <span class="keyword">~</span> <span class="symbol">mpg</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">subset</span> <span class="argument">=</span> <span class="keyword">(</span><span class="symbol">gear</span> == <span class="number">4</span><span class="keyword">)</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/bwplot3.svg" class="plot" /></div></div>


---


# Scatterplots #

---

### Basic Scatterplot ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot1.svg" class="plot" /></div></div>


---

### Solid Circles as Points ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">)</span> <span class="comment"># change point shapes using pch</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot2.svg" class="plot" /></div></div>


---

### Change Color of Points ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'maroon'</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot3.svg" class="plot" /></div></div>


---

### Add xAxis and yAxis Labels ###


<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'maroon'</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">,</span>
  <span class="argument">xlab</span> <span class="argument">=</span> <span class="string">'Weight'</span><span class="keyword">,</span> <span class="argument">ylab</span> <span class="argument">=</span> <span class="string">'Miles Per Gallon'</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot4.svg" class="plot" /></div></div>


---

### Color Points by Categorical Variable ###


<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">group</span> <span class="argument">=</span> <span class="symbol">cyl</span><span class="keyword">,</span> <span class="argument">auto.key</span> <span class="argument">=</span> <span class="number">TRUE</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">,</span>
  <span class="argument">xlab</span> <span class="argument">=</span> <span class="string">'Weight'</span><span class="keyword">,</span> <span class="argument">ylab</span> <span class="argument">=</span> <span class="string">'Miles Per Gallon'</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot5.svg" class="plot" /></div></div>


---

### Split by Single Categorical Variable ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span> <span class="keyword">|</span> <span class="symbol">cyl</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'maroon'</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">,</span>
  <span class="argument">xlab</span> <span class="argument">=</span> <span class="string">'Weight'</span><span class="keyword">,</span> <span class="argument">ylab</span> <span class="argument">=</span> <span class="string">'Miles Per Gallon'</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot6.svg" class="plot" /></div></div>


---

### Split by Multiple Categorical Variable ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span> <span class="keyword">|</span> <span class="symbol">cyl</span> <span class="keyword">+</span> <span class="symbol">gear</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">col</span> <span class="argument">=</span> <span class="string">'maroon'</span><span class="keyword">,</span> <span class="argument">pch</span> <span class="argument">=</span> <span class="number">16</span><span class="keyword">,</span>
  <span class="argument">xlab</span> <span class="argument">=</span> <span class="string">'Weight'</span><span class="keyword">,</span> <span class="argument">ylab</span> <span class="argument">=</span> <span class="string">'Miles Per Gallon'</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot7.svg" class="plot" /></div></div>


---

### Scatterplot for a Subset of the Data ###

<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr"><span class="functioncall">xyplot</span><span class="keyword">(</span><span class="symbol">mpg</span> <span class="keyword">~</span> <span class="symbol">wt</span><span class="keyword">,</span> <span class="argument">data</span> <span class="argument">=</span> <span class="symbol">mtcars</span><span class="keyword">,</span> <span class="argument">subset</span> <span class="argument">=</span> <span class="keyword">(</span><span class="symbol">cyl</span> == <span class="number">6</span><span class="keyword">)</span><span class="keyword">)</span>
</pre></div></div><div class="rimage center"><img src="figure/scplot8.svg" class="plot" /></div></div>


---

# Subset #

---








