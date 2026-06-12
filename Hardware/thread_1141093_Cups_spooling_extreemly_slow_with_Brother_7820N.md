---
title: "Cups spooling extreemly slow with Brother 7820N"
date: 2009-04-28
forum: Hardware
---

### Post by fili on 2009-04-28
Cups does recognize my Brother 7820N printer and it does work, but it's very slow in spooling.
When printing a document with multiple pages the printer reaches its maximum capacity of 20 ppm.
When printing out multiple files (each file a page long) it does it with a pause of 30 seconds (!) between pages.
I regularly have to print out ~100 pdf-files at once, making it ~50 minutes job. Which is quite annoying.
I've tried different drivers and also installed the brother-cups-wrapper-laser package, alas without any noticeable speed improvement.

Is there a way to make cups spool faster.
Is it a driver problem? Or do all printers print-out multiple files this slowly on Ubuntu?
Does anyone have any tips/suggestions of where to look next?

Thanks in advance,
Fili

---

### Post by fili on 2009-04-28
Okay it seems i've solved my own problem.
For anyone looking for the answer, here is what i missed:

It seems that after installing the brother-cups-wrapper-laser package (other brother printers have a package with a slightly different name, search for it in synaptic/aptitude) some new drivers appeared in the cups driver select wizard. After selecting the "MFC7820N for Cups" driver spooling is much much faster.

Regards,
Fili

---

