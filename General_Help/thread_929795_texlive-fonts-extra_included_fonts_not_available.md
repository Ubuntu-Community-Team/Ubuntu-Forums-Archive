---
title: "texlive-fonts-extra included fonts not available?"
date: 2008-09-25
forum: General Help
---

### Post by rattusdatorum on 2008-09-25
hi,

I just wanted to use the "duerer" ([http://texcatalogue.sarovar.org/entries/duerer-latex.html](http://texcatalogue.sarovar.org/entries/duerer-latex.html)) font in LaTeX. Well, duerer.sty not found (kile), hence I googled. 
It turns out, it is in the the texlive-fonts-extra package ([http://packages.ubuntu.com/hardy/texlive-fonts-extra](http://packages.ubuntu.com/hardy/texlive-fonts-extra)).
Well, apt-get install reveals I have the current version, although it mentions that this package was manually installed.
I also checked the bug reports of the package -> non for duerer.

Anyone was a clue?
I guess it could be due to the manual installation, yet, how can I solve this.

I would be very glad if you could help me, thx in advance.

Bernhard

---

### Post by mirx on 2009-04-14
> **rattusdatorum said:**
> hi,

I just wanted to use the "duerer" ([http://texcatalogue.sarovar.org/entries/duerer-latex.html](http://texcatalogue.sarovar.org/entries/duerer-latex.html)) font in LaTeX. Well, duerer.sty not found (kile), hence I googled. 
It turns out, it is in the the texlive-fonts-extra package ([http://packages.ubuntu.com/hardy/texlive-fonts-extra](http://packages.ubuntu.com/hardy/texlive-fonts-extra)).
Well, apt-get install reveals I have the current version, although it mentions that this package was manually installed.
I also checked the bug reports of the package -> non for duerer.

Anyone was a clue?
I guess it could be due to the manual installation, yet, how can I solve this.

I would be very glad if you could help me, thx in advance.

Bernhard

You can copy the files manually:
1. go the the mentioned url above ([http://mirror.aarnet.edu.au/pub/CTAN/macros/latex/contrib/duerer-latex/](http://mirror.aarnet.edu.au/pub/CTAN/macros/latex/contrib/duerer-latex/))
2. Download the duerer.sty file and the four *.fd files
3. (as root) create a duerer directory in your:
   /usr/share/texmf-texlive/tex/latex/ directory
4. copy the files you have downloaded in that directory.
5. execute texhash and all is done.
Cheers,

---

### Post by jaguarviajero on 2009-08-29
Hello,

i have the same problem. i want to use the antiqua or garamond font but can not.

what is the point of installing the texlive-fonts-extra package (with synaptic or manually) if you still have to download each font? why doesn't the package contain the .sty files? is it a bug?

or rather, have i forgotten to do something?

thanks in advance for the support

---

### Post by migge on 2010-04-22
You need to download the actual (non-free) fonts using:
```
sudo getnonfreefonts-sys -a
```

---

