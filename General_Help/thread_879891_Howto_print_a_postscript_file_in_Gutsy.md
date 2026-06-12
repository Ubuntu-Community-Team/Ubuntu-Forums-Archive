---
title: "Howto print a postscript file in Gutsy?"
date: 2008-08-04
forum: General Help
---

### Post by AchimRS on 2008-08-04
Hi,
I guess it is a very stupid question, but for now I couldn't find any solution.
I have a .ps PostScript file (printed on a Windows machine with a PS driver fitting to that printer connected to my Gutsy machine), which I want to print including all formatting and layout under KUbuntu Gutsy.

What is the simplest way to print the ps file?

Thanks
  Achim

---

### Post by mannheim on 2008-08-04
If you open a terminal and do:
```
lpr filename.ps
```
then that should print the postscript file "filename.ps" to your default printer. (Alternatively, double-click on the postscript file to open it in whatever document-viewer is the default; then just select "Print" from the File menu.)

---

### Post by AchimRS on 2008-08-04
The console command lpr prints nonsens, three pages of paper with e.g. "ERROR invaldfont", "STACK:"... an some other stuff.

And within KDE is no application registered to react on the double-click, so Kate is starting and showing me the ASCII sources of the .ps file.

What document-viewer do you mean for example in KDE is responsible for PostScript files and able to print it???

---

### Post by x1a4 on 2008-08-04
Try printing with the **-l** option.  A PostScript file is already formatted for the printer so it might be necessary to disable filtering.
```
lpr -l file.ps
```
Also, ensure you have the **PRINTER** environment variable set to the correct name of the printer you want to print with.  Otherwise use the **-P** option.  
```
lpr -P PrinterName file.ps
```

You may also want to try the **cupsdoprint** tool.  It's a KDE command line tool to print files.  See the **cupsdoprint** man page for details.

As for the viewer, install the **kghostview** package.

EDIT: post the error messages.  From what you posted it looks like the document might be using a font you don't have installed.

---

### Post by AchimRS on 2008-08-04
Thanks a lot thats it:
I tried KGhostView (of course, I prefere KDE over command-line :-). It was installed, but not visible in the "K" Menue, so after manually adding it there I was able to start it also from within the menue.
The next problem was, that it was not able to render my .ps files. The file was generated from the PostScript printer driver of a Windows XP machine. KGhostView simply shows nothing when opening the generated files, all pags are white. But when trying to print it, the preview function and the printed paper contains all I need.

Thanks for the fast answers
  Achim

---

### Post by editrix on 2008-08-05
First off, please mark the thread solved, so others can benefit from your answers.

Then, the reason you can't see anything _may_ be a font issue. That is, the fonts Win used aren't installed in KDE. If you're dual booting, you can just symlink your Win fonts directory to a Fonts directory in Ubuntu (I did that so long ago I can't remember how, now, but you can google symlink).

---

### Post by x1a4 on 2008-08-05
> **editrix said:**
> (I did that so long ago I can't remember how, now, but you can google symlink).
```
ln -s TARGET LINK_NAME
```
or using Konqueror just drag the file from one directory to another and select you want to create a symlink from the menu.

---

