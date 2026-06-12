---
title: "Cannot view R vignettes due to Ubuntu system settings"
date: 2008-11-15
forum: General Help
---

### Post by lbthrice on 2008-11-15
Hello all,

I am trying to view an R vignette.
Here is the situation: I issue the openvignette(), then select the vignette I wish to view...and the system returns:

```
Could not get a file descriptor referring to the console.
```

This action should spawn a ps viewer displaying the contents of the vignette for my enjoyment.
I suspect it may have something to do with the call to the postscript viewer application.

Any Thoughts?


Here is the copy paste of my session

```
> openVignette()
Please select a vignette:  

 1: annotate - Annotation Overview
 2: annotate - Basic GO Usage
 3: annotate - HowTo: Get HTML Output
 4: annotate - HowTo: use chromosomal information
 5: annotate - HOWTO: Use the online query tools
 6: annotate - Using Affymetrix Probe Level Data
 7: annotate - Using Data Packages
 8: annotate - Using the homology package
 9: AnnotationDbi - AnnotationDbi
10: AnnotationDbi - SQLForge
11: Biobase - An introduction to Biobase and ExpressionSets
12: Biobase - Bioconductor Overview
13: Biobase - esApply Introduction
14: Biobase - Notes for eSet developers
15: Biobase - Notes for writing introductory 'how to' documents
16: Biobase - quick views of eSet instances
17: geneplotter - How to assemble a chromLocation object
18: geneplotter - Visualization of Microarray Data
19: xtable - xtable Gallery

Selection: 17)
Opening /home/lbthrice/R/i486-pc-linux-gnu-library/2.8/geneplotter/doc/byChroms.pdf 
> Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console
```

---

### Post by lbthrice on 2008-11-18
for a workaround see 
[http://www.nabble.com/unable-to-view-vignette-in-R-td20521730.html]("http://www.nabble.com/unable-to-view-vignette-in-R-td20521730.html")

---

