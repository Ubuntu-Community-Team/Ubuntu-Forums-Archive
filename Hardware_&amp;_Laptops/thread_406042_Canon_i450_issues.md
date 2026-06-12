---
title: "Canon i450 issues"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by sethmahoney on 2007-04-10
I just had to do a fresh Edgy 6.10 install and my Canon i450 is no longer working correctly.  The bjc800 driver prints the whole page, but tiny, in the upper left hand corner, and the gutenprint driver prints the page in the correct size, but it is very light.  Any suggestions?

The [OpenPrinting database]("http://openprinting.org/show_printer.cgi?recnum=Canon-i450") says to use the bjc800 driver, but that "You have to adjust the resolution values in the ppd to the correct values: 150x150, 300x300, 600x600 and 1200x1200."  It doesn't look like I can do that in the GNOME configuration utility - any ideas what that might mean (and if it might work)?

---

### Post by junjan on 2007-05-08
In Feisty I have been trying several combinations, none of them very good until I selected the "BJC-7000 model" with the "Gutenprint CUPS driver (expert)"  (tweaking a bit the color controls). It  gives quite good results, not perfect but acceptable.

Hope it helps in your case. :)

---

### Post by chajuram on 2008-06-29
Thank you Junjan. With 8.04 my printer is usable again!!

> **junjan said:**
> In Feisty I have been trying several combinations, none of them very good until I selected the "BJC-7000 model" with the "Gutenprint CUPS driver (expert)"  (tweaking a bit the color controls). It  gives quite good results, not perfect but acceptable.

Hope it helps in your case. :)

---

