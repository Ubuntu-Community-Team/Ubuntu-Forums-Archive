---
title: "Graphing System"
date: 2008-10-26
forum: General Help
---

### Post by Jaded Misanthrope on 2008-10-26
Could anybody recommend a program (ideally GNOME, but I'd manage with another type) capable of graphing a given function and, ideally, predicting the function of a graph given a series of points on it?

---

### Post by dracayr on 2008-10-26
gnuplot is the classic program for this. it's even installed by standard (I think)

EDIT: it's CLI, though

dracayr

---

### Post by mbeach on 2008-10-26
Graphmonkey (in the repos - can install through synaptic) might do what you want
[http://graphmonkey.sourceforge.net/](http://graphmonkey.sourceforge.net/)

For the second part, I believe Open office calc can come up with the formula given a set of points (displaying function on chart).  Not sure about that, but I seem to remember excel being able to do that a few years back.

---

### Post by mbeach on 2008-10-26
yes, open office calc (ver3 at least) can create an x-y scatter plot, and show the equation and r value on the chart.  

Create the columns of points for x and y, select them, click Insert -> Chart, choose the xy scatter, accept all the defaults (or amend as necessary).  When the chart is drawn, right click on the data series in the chart, select "insert trendline", pick the regression type, and check the show equation and correlation coefficient if desired -> Ok button.

edit
oo calc 2.4 does not appear to have the 'insert trendline' feature (not to me anyway)

---

### Post by skintythe1andonly on 2008-10-26
qtiplot is very similar to origin if you have any experience with it. it is easy to use anyways. It is used for data analysis fitting fuctions to data points, and does give excellent error analysis. It can then export professional looking graphs if they are to be presented. If it is functions rather than data points you are trying to work with...then something like Maxima (Wxmaxima if you want a GUI). For a full math package try octave (it uses gnuplot for graphs). Im currently looking at sage tho at the moment...but it looks like it needs a bit of reading first.

I know im rambling....try qtiplot seriously, its in the repos.

---

