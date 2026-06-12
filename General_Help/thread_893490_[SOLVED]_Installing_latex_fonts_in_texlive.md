---
title: "[SOLVED] Installing latex fonts in texlive"
date: 2008-08-18
forum: General Help
---

### Post by jbergfel on 2008-08-18
I am trying to install a font that I downloaded from [HTML]http://www.ctan.org/tex-archive/fonts/initials/[/HTML], but so far I haven't succeeded. The font is called Gotische Initialen and the short name is GotIn

I have downloaded GotIn.afm, GotIn.fd, GotIn.pfb, GotIn.tex, GotIn.tfm, config.GotIn and put them in one map. But when I run ```
pdflatex GotIn.tex
``` it returns the message:

```
kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 6+0/600 --dpi 3600 GotIn
mktexpk: don't know how to create bitmap font for GotIn.
kpathsea: Appending font creation commands to missfont.log.
(see the transcript file for additional information)
```

I also tried to copy the GotIn.map, GotIn.pfb, GotIn.tfm, GotIn.afm to the appropiate maps in /usr/share/texmf-texlive/fonts and then run texhash and updmap, but after this running pdflatex gives me the same error.

Does anybody know how to install this font (or at least make the GotIn.tex produce a correct pdf file)?

---

### Post by tacutu on 2008-08-18
best to create a local texmf hierarchy in your home folder. Now, in /home/USERNAME/texmf, you put your fonts as follows:
*.afm files in fonts/afm/initials/
*.tfm in fonts/tfm/initials/
*.fd in tex/latex/initials/
*.pfb in fonts/type1/initials/
*.map in fonts/map/

don't forget to run texhash afterwards and ```
updmap --enable Map=GotIn.map
```.

Hope I don't forget any steps...

---

### Post by jbergfel on 2008-08-18
Thank you tacutu, your instructions worked fine and my problem is solved.

---

### Post by tacutu on 2008-08-18
Glad to be of assistance! Maybe you should mark the thread as sloved.

---

### Post by briantk_1988 on 2009-03-12
Hi!

I tried to install Lucidabright to my TeXlive 2007 under Kubuntu.  After dong that, I can compile my document without any error but instead of using the lucidabright, it uses computer modern instead.  In installed this on my MikTeX system on Windows and it works fine.

Could someone please help me?

Thanks!!!!!

Brian

---

### Post by chaanakya_chiraag on 2010-10-15
I am having the same problem as the original poster while trying to use the font hge:
```
http://www.ctan.org/tex-archive/fonts/hge/
```
Since it only provides an mf font, I'm not sure how to proceed.  It works when I keep the font in the same folder as the document, but fails when I move it to a local texmf structure and try to compile the document.  It fails with the same error message as the op.  Does anyone know how to proceed?

---

### Post by chaanakya_chiraag on 2010-10-15
Never mind...I made LaTeX create the files in the appropriate places by running it with hge.mf in place and then deleting it.  Does anyone have an automated way to install LOTS of fonts (like every single font under the fonts directory)?

---

