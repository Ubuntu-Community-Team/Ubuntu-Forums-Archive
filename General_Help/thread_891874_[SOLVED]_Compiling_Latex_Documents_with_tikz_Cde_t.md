---
title: "[SOLVED] Compiling Latex Documents with tikz Cde to dvi"
date: 2008-08-16
forum: General Help
---

### Post by cyberslayer on 2008-08-16
Hi,

I am using the texlive packages in Hardy Heron and have been having a problem using Latex with tikz.  The problem is that when I compile a .tex document that contains the tikzpicture environment to dvi using the latex command, the text in the tikzpicture is visible but the graphics are not.  I've attached a simple example of a .tex file I created to illustrate this along with the resulting .dvi and .log files.  I know evince does not display the images referenced in .dvi files properly so I used xdvi to view the file but it still looks the same.  When I use pdflatex instead of latex to compile the .tex file to pdf everything works fine and I get the attached .pdf file with the .log file named test-pdf.log (the name was changed from test.log after it was generated).  Anyone know how to fix this problem?

Thanks

---

### Post by tacutu on 2008-08-21
as per tikz documentation, you should convert the dvi file to a ps file to see the results:
```
dvips filename.dvi -o
```

---

### Post by cyberslayer on 2008-08-24
Ok, it works now.  I did look in the manual before posting but I guess I missed that.  Thanks for the help.

---

