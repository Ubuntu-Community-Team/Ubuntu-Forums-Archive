---
title: "How do you set screen resolution on a TFT when it reports the wrong resolution?"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by cucaracha on 2007-01-14
I am trying to set up a new 1400x900 widescreen monitor, but I just cannot get it to work correctly. The closest I get is 1400x900, which causes lots of vertical blur bands.

I have tried with two different machines with i945 and ATi cards, Ubuntu 6.06, 6.10, always with the same result.

My investigations indicate that the monitor reports itself to be "1440x900". It also supports 1600x1200 by squashing the pixels together, so it also advertises support for that resolution, which messes things up.

According to the documentation I have seen online, disabling DDC (using NoDDC and DCC "off") and setting the correct modeline should work, but it always reverts to 1440x900 (if I am lucky).

Any ideas on how to force it to the right resolution? It really is driving me nuts not being able to use the monitor to the native resolution.

Thanks

Gabriel

---

### Post by blackened on 2007-01-15
Post your xorg.conf and we'll see what we can do.

---

### Post by robenroute on 2007-01-15
If you run "dpkg-reconfigure xserver.xorg" as sudo (from the command line that is), can you choose the correct resolution?

---

### Post by bigken on 2007-01-15
try sudo dpkg-reconfigure phigh xserver-xorg

---

