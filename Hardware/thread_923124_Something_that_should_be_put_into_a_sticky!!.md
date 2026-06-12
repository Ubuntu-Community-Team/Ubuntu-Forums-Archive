---
title: "Something that should be put into a sticky!!"
date: 2008-09-18
forum: Hardware
---

### Post by water_foul on 2008-09-18
A default xorg config file that is guaranteed to work on 90% of computers for those that the commands don't work, I had a problem with the commands and I eventually found out it was that I needed to set the driver to use, which wasn't put in there bu xfix or dpkg-reconfigure, so I ended up putting vga on, borrowed from the output of Xorg -configure, which caused more problems when all i needed to dod was swap out vga for vesa... If that information was readily available, as a failsafe, then it cause less problems. I thinking in the default it should use vesa, have a basic ps2 mouse, and a basic keyboard... I don't have the know-how to do this but I think it needs to be done

---

### Post by dustman on 2008-09-18
well...when I had troubles with the xorg config file (added some crap settings and all went to hell), I just started the Ubuntu live CD, and copied the config file from there after the X server started.

---

