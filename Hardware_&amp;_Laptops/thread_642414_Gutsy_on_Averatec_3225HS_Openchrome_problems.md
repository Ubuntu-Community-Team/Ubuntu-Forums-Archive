---
title: "Gutsy on Averatec 3225HS Openchrome problems"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by markmaus on 2007-12-16
I'm trying to install Gutsy i386 on an Averatec 3225HS laptop and have 3D acceleration working.  Under Feisty I could use the "via" driver in xorg.conf and add the following modifiers:
Option  "EnableAGPDMA"
Option  "DisableIRQ"
and everything worked fine (Tux Racer, GLGears, etc.)
With Gutsy, this approach will no longer enable 3D effects and TuxRacer will lock up the machine hard.  
I have installed the openchrome driver using several techniques, and I can't even get X to load.  If anyone has the same laptop, AV3225HS or similar, and has Openchrome working, please let me know what the trick is and what your /etc/X11/xorg.conf looks like.
Thanks,

---

