---
title: "Stellarium wont start"
date: 2008-09-18
forum: General Help
---

### Post by roger_1960 on 2008-09-18
Hi

Have installed Stellarium using synaptic - no errors. (Have tried removing and reinstalling with the same result) On trying to run from GUI, nothing happens.  On trying to run from terminal I get:

roger@acer2laptop:~$ stellarium
stellarium: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
Aborted
roger@acer2laptop:~$

Does anyone have any ideas? Is this a hardware problem?

Its on Ubuntu 8.04.1 with an Acer Aspire 1353LC (French keyboard) with 756Mb ram

---

### Post by malachi1990 on 2008-09-29
What's your video card.  You may have to download the proprietary drivers to use it, as the vesa driver doesn't work with stellarium.

---

### Post by roger_1960 on 2008-09-30
Hi

Thanks for the interest. (I've spent hours checking this out since my post) Its a VIA chip  VT8378 [S3 UniChrome] which currently seems to have no proprietary Unichrome driver support in Hardy- its OK with Gutsy but that driver doesn't work.  Hopefully, if I wait a few months the new driver will appear!  Its an oldish laptop so I'm not too worried.

If anyone knows otherwise, it would be good to know.......

---

