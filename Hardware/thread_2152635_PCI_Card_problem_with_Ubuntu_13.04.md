---
title: "PCI Card problem with Ubuntu 13.04"
date: 2013-06-08
forum: Hardware
---

### Post by Herber on 2013-06-08
I am trying to get a Dell Dimension B110 working with Ubuntu 13.04.  I was originally unable to run Ubuntu 13.04 because the integrated graphics on the Celleron 80546 processor was incompatible with Ubuntu 13.04 so I used Lubunutu instead.  Unfortunately Flash doesn't work in Lubuntu on the integrated graphics.  So I bought a PCI based NVIDIA card off ebay and installed it along with Ubuntu 13.04.  The problem was solved until yesterday when I got this message on boot:

process: 216 pango-critical **: pango_font_description_better_match: assertion `(null)' failed

The computer boots to this message and a blank screen, I can't ctrl^alt anything, no command prompt.  Can only shutdown by holding the power button down.

I am suspicious this has to do with the integrated graphics and the PCI card but I don't know what to do now?

---

### Post by searchfgold6789 on 2013-06-08
Which graphics card was it? Did this happen after running updates?
First, try checking your BIOS. Disable the integrated graphics card, if possible.
You could try booting into recovery mode. If you didn't install proprietary drivers, do so from there, or reinstall them if you did.

---

### Post by Herber on 2013-06-08
Thanks, the BiOS adjustment did the trick.

---

