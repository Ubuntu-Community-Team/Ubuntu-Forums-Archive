---
title: "i810 broken for Thinkpad R50e"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by leandir on 2006-12-11
I finally found out what is the cause for suspension not working on my Thinkpad R50e: it is the very graphics card driver! I am sure about it,here is my evidence:

1- reinstalled the i810 driver because the vesa one is not able to use the card properly (googleearth not functioning for example)
2- tried to go into suspension, the come out is broken - graphics completely gone
3- changed the driver from i810 to vesa in the xorg.conf from console session and killed Xorg
4- graphics completely restored, no more problems with suspension

This is FAR from an optimal solution though, as I do not have a proper driver for my graphics card! Does someone know where I should file the bug report?

---

