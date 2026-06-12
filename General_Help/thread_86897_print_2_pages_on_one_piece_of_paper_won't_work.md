---
title: "print 2 pages on one piece of paper won't work"
date: 2005-11-06
forum: General Help
---

### Post by basfrank on 2005-11-06
Dear forum,

hp psc 1610 via hplip/hpijs 

Problem: 
I want to print a 23 pages pdf-file with the 'print 2 pages on one sheet of paper' option. I can choose this option in the evince 0.4.0 options dialouge. 
But the printer prints one page per sheet of paper. 
Why is this? How can I print the way I want? 
Does anyone have the same problem? 
Please help me solve this issue.

---

### Post by RikoW on 2005-11-07
Hi,

I'm not sure what evince is, but you can create a temporary pdf file using 
the pdfnup package (it's in the repos).

From a pdf file you can create a nxm page pdf version for printing by

```
pdfnup --nup 1x2 --orient portrait --frame true --delta "2cm 2cm" --offset "0.5cm 0.5cm" --paper a4paper --scale 0.8 file.pdf
```

This creates a 2 page / sheet version in portrait of file.pdf.

Check the man page of pdfnup for explanation of the options.

Hope that helps,

             Riko

---

### Post by basfrank on 2005-11-07
Evince is a pdf viewer based on xpdf as far as I know.
It's the standard for viweing pdf in Ubuntu.
Thankx for your help. I'll try it.

---

### Post by mvandeg on 2005-11-07
To prevent confusion, pdfnup is in the pdfjam package. For me a simple

```
pdfnup --nup 2x1
```

did the trick.

---

