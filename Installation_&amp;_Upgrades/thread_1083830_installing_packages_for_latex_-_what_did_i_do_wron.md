---
title: "installing packages for latex - what did i do wrong?"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by christinak on 2009-03-01
Hello!

I am writing something in latex, and need a package (bbm) that is not in the general latex package.

I downloaded it as a .zip file, moved this to /usr/share/texmf-texlive/tex/latex/ , unzipped it, read the readme, and then did latex bbm.

So, I now have a folder there with bbm.sty inside.

However, when I want to latex my code, it tells me [HTML]Master.tex:5:File `bbm.sty' not found. \usepackage[/HTML] which is bad.

I then moved the whole file to /usr/share/texmf/tex/latex/, which did not work either.

So, i figured i'd google for a bit and found [http://blog.irrepupavel.com/2007/02/installing-latex-style-files-sty-on.html](http://blog.irrepupavel.com/2007/02/installing-latex-style-files-sty-on.html) - so I went into (both) the files where I had my bbm.sty, and did the ```
sudo mktexlsr
``` thing - now, I get a new error when compiling, 

```
Master.tex:168:Font U/bbm/m/n/10.95=bbm10 at 10.95pt not loadable: Metric (TFM) file not found. \mathbbm{1}
```, for whenever I am using the bbm-style. 

What am I doing wrong? 

I would appreciate any help!

Cheers,
Christina

What am I missing?

---

### Post by seventeener on 2009-03-04
hi, install the package texlive-fonts-recommended

---

### Post by zsoltl on 2009-04-03
The needed package is actually texlive-fonts-extra

---

