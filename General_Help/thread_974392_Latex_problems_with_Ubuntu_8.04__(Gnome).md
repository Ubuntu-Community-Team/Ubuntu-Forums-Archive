---
title: "Latex problems with Ubuntu 8.04  (Gnome)"
date: 2008-11-07
forum: General Help
---

### Post by StephaneG on 2008-11-07
Hi there,
I have installed texmaker using synaptic package manager from Ubuntu 8.04 but I cannot get it to work, whenever I launched the pdf viewer, I get the same error message (after saving the file as a tex file) :

Process started

Process exited with error(s)

Can anyone help please?
I am new to Linux and Ubuntu.
Also, if anyone could explain how to install the plugin that works with Gedit that would be great.
I want to stick to Gnome therefore Kile is not really an option, and texmacs is not a real Latex application.
Thanks.
Stephane

---

### Post by conscious on 2008-11-07
IIRC the default setting for texmaker is to use xpdf for viewing PDFs. In texmaker, go to Settings -> Texmaker settings -> Commands and change "xpdf" to "evince" in the "PDF viewer" field. (And Evince should probably be used as DVI and PS viewer as well.)

---

### Post by Stefan_K on 2008-11-07
Hi Stephane,

> **StephaneG said:**
> 
I want to stick to Gnome therefore Kile is not really an option

I'm using Kile on GNOME since Ubuntu 7.04. I'm very satisfied with it and I never encountered problems during my work, producing hundreds of LaTeX documents, no problem with any other application. I'm preferring to benefit from the advantages of Kile instead of feeling better just because I wouldn't have KDE packages on my system.
Of course it's great to have Texmaker as alternative. By the way, Texmaker 1.8 has been [released]("http://texblog.net/latex-archive/ide-editor/texmaker-18/").

Stefan

---

### Post by StephaneG on 2008-11-09
Hi conscious,
I changed what you indicated and something happened indeed but now it says:
Unable to open the document
unknown mime type

Thanks Stefan,I´ll try kile if I cannot get this one to work.

---

### Post by Malet on 2008-11-09
personally I'd just
```

sudo apt-get install tetex-bin
```

then you can just do:```
latex filename.tex
```
in console, or pdflatex for pdfs.

---

### Post by Stefan_K on 2008-11-09
Hi Malet,

> **Malet said:**
> personally I'd just
```

sudo apt-get install tetex-bin
```

tetex has been obsolete since years, see [de-support notice]("http://www.tug.org/tetex/"). texlive is recommended instead and could be installed in a similar way.

Stefan

---

### Post by ad_267 on 2008-11-09
Have a look at the LaTeX plugin for Gedit. [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)
It requires rubber to compile documents.

---

### Post by StephaneG on 2008-11-11
Ok I´ve downloaded the plugin but the install file is blank...how do I intall it then?
Can anyone help me get texmaker to work?
Thanks

---

### Post by ari807 on 2008-11-21
Maybe this page can help you. [http://www.exomatik.net/LaTeX/USBTeXEnglish](http://www.exomatik.net/LaTeX/USBTeXEnglish)

You have to download : 
:KS-MiKTeX 2.7 portable version 
:KS-Ghostscript 8.53 
:KS-Ghostview 4.7 
:KS-SumatraPDF 1.7 
:KS-Texmaker 1.6 
and after that :popcorn: you have to download USBTEX that helps compile your documents without configuration of TEXMAKER. 
then follow the Instructions.

---

### Post by edog76 on 2008-11-26
I'm assuming you have already installed the Texlive package. When you save the file in Texmaker you have to manually add the ".tex" to the end of the file name. Have you done that?

If so, then can you post what the summary of the error messages when you try to pdflatex or latex the file?

---

### Post by StephaneG on 2008-11-26
Hi edog,yes I´ve installed texlive and I added by hand the .tex while saving but the problem remains and I get the error message (mime) mentioned before.
Regards
Stéphane

---

### Post by Idefix82 on 2008-11-26
To install the Latex plugin is easy and gedit with this plugin is an amazing tool for Latex. Go to this page: [http://sourceforge.net/project/showfiles.php?group_id=204144&package_id=243533&release_id=612646]("http://sourceforge.net/project/showfiles.php?group_id=204144&package_id=243533&release_id=612646")
download the plugin and save the tar ball on your Desktop. Then type this in the terminal:
```
cd ~/Desktop
tar -xzf LaTeXPlugin-0.1.3.2.tar.gz
cp -R LaTeXPlugin-0.1.3.2/plugins/* ~/.gnome2/gedit/plugins

```

Now just open Gedit and activate the plugin - done. If you want to use the compile functions of the plugin, you need to install rubber:
```
sudo apt-get install rubber
```

Let me know how it works out.

---

### Post by edog76 on 2008-11-26
The mime error occurs when you click the "view pdf" button, correct? What happens when you click "pdflatex"? Are you getting error messages then?

---

### Post by StephaneG on 2008-11-27
Hi Edog, yes it´s what happens, and when I use another format like pdflat I get this :

Process started

Process exited with error(s)

---

### Post by edog76 on 2008-11-27
Okay, my guess at the moment is that you cannot view the pdf b/c there is some problem in the syntax preventing a pdf from being made.

Try creating a simple document and see if pdflatex will work w/o error
```
\documentclass{article}
\begin{document}
This is a document
\end{document}
```
If it works, then click on the "view pdf"

---

### Post by StephaneG on 2008-11-28
Ok, where should I type that, in a new texmaker file? (I´m new to all this stuff)
Thanks.

---

### Post by edog76 on 2008-11-28
Yes, just make a new file, then copy and paste the above and save it as a .tex file, then run "pdflatex" and we'll see what happens.

---

### Post by StephaneG on 2008-11-28
Yes it works,thanks!
What do I need to do to be able to view my other files?Should I include this program everytime and write the rest in the middle?

---

### Post by edog76 on 2008-11-28
You're welcome, glad it's working now.

I would suggest this site:
[http://www.tex.ac.uk/tex-archive/info/beginlatex/html/intro.html#intro](http://www.tex.ac.uk/tex-archive/info/beginlatex/html/intro.html#intro)

and the guide listed midway down the page "A Not So Short Introduction" to get a good handle on what you can do with LaTeX.

You could just use the above and type whatever you want typeset between the \begin and \end tags, but that would be massively under utilizing LaTeX.

---

### Post by StephaneG on 2008-11-29
That´s cool,I'll look into it.
Thanks again.
Stéphane

---

