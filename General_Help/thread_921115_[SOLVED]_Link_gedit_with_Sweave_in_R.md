---
title: "[SOLVED] Link gedit with Sweave in R"
date: 2008-09-15
forum: General Help
---

### Post by pofigster on 2008-09-15
I just learned how to link Gedit with R so I can run R code from inside Gedit.  Now I'm curious - would it be possible to use an "External Command" to launch R and run the Sweave command on the .rnw file currently open?  Heck, getting one step better, could I then (in the same command) run latex to make a PDF?

In case you know the answer but don't use R, R is a statistical programming package.  When running R you can issue a command Sweave("name of file") which will parse all R code inside a TeX document and produce a .tex file which can then be parsed into PDF or whatever.

---

### Post by pofigster on 2008-09-16
Alright, so, I figured it out with the help of a friend and Google.  After installing the LaTeX plugin (you can [download it here]("http://live.gnome.org/Gedit/LaTeXPlugin")) there is a native option for building the .rnw file called "R Sweave PDF" (don't know how I missed it).  But it doesn't work by default.

Under Edit-Preferences and then the tab Plugins, you can edit the LaTeX plugin.  After you click "Configure Plugin" you'll want to click on the tab in the new window called "Build Options"

Scroll down to the R Sweave PDF and click "Edit"

The first problem (and this is a problem everybody will have) is that the first command is
```
R Sweave %e.Rnw
```
The correct command is
```
R CMD Sweave %e.Rnw
```
or if you're like me and name your files .rnw
```
R CMD Sweave %f
```
After you make the change, hit your Enter button to save the change (it's really finiky for me.

Now, your LaTeX PDF Build code is still probably saying "Rubber"  Maybe you have this installed, or maybe you installed TeXLive like I did.  If you installed TeXLive, you'll want to change the code on the second line to:
```
pdflatex -interaction=nonstopmode %e.tex
```
and then make sure that the Processor is set to Default (it's a drop box just to the right of the command).

Hope this ends up helping somebody in addition to me!

---

### Post by gruntlips_ on 2008-09-26
So how did you get gedit to run R code directly? I can't seem to figure that one out.

Thanks.

- ccc

---

### Post by samden on 2008-12-09
I and many others would like to know how you did that too.

---

### Post by hugmenot on 2008-12-10
BTW, Rubber is not an alternative to TexLive but rather a cool, little python program that automates the compilation of LateX to PDF. It deals with all the re-running of pdflatex and bibtex, etc. So with rubber you only need one command and it outputs the errors and warnings in a much cleaner format.

It&#8217;s in the repos.

---

### Post by roems on 2009-10-03
> **samden said:**
> I and many others would like to know how you did that too.

There is a plugin for gedit called Rgedit, it allows you to run your R script to the console. See [http://live.gnome.org/Gedit/Plugins]("http://live.gnome.org/Gedit/Plugins").

You have to download the file, extract the folder and place it in ~/.gnome2/gedit/plugins folder. Then open gedit and go to Edit Preferences Plugins and enable it.

HTH,

Roberto

---

### Post by It_newbiie on 2009-10-17
Hi pofigster

I have wanted the same feature as you, and now I am so happy that you post the resolution. I have followed the steps you described, only I keep the rubber part, coz I have that installed. I load a .rnw file, but dont get the option to 

R sweave -> pdf

please help!

---

### Post by StuartN on 2009-10-17
> **roems said:**
> There is a plugin for gedit called Rgedit, it allows you to run your R script to the console. See [http://live.gnome.org/Gedit/Plugins]("http://live.gnome.org/Gedit/Plugins").

That is the best Linux tip I have seen in a long time. I have struggled with R Commander and tkl interfaces, but having a direct run out of an editing environment is brilliant.

Man thanks.

---

