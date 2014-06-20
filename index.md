---
title       : Clustering using the k-means algorithm
subtitle    : 
author      : Pieter Huibers 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## K-Means Clustering

The Shiny app I wrote illustrates the use of the k-means clustering algorithm in R.

K-means clustering works by identifying the center of a number of clusters (you can define how many clusters)
and then assigns data point to each of these clusters based on the distance of the data point to a specific cluster
center.

---

## Data Point Generation

The data points are generated using the `rnorm()` function. The number of data points to be generated is taken from the
first slider input in the Shiny app and passed as a parameter to the `rnorm()` function.

```r
x <- rnorm(5)
y <- rnorm(5)
data <- data.frame(x,y)
data
```

```
##          x       y
## 1 -0.14451 -0.2283
## 2  1.43436 -0.2738
## 3 -1.52019 -0.6193
## 4  0.04922  1.4443
## 5  1.11214 -0.2438
```

---

## Clustering

Then the data points are clustered. The number of clusters to use is determined by the value of the second input slider
in the Shiny app.

```r
fit <- kmeans(data , 2)
aggregate(data,by=list(fit$cluster),FUN=mean)
data <- data.frame(data, fit$cluster)
```

---

## Usage

To use the Shiny app go to [https://pieterhuibers.shinyapps.io/clustering/](https://pieterhuibers.shinyapps.io/clustering/). You can use the first slider to set the number of random data points that are generated. You can use the second slider to set the number of clusters in which the data points will be divided.
