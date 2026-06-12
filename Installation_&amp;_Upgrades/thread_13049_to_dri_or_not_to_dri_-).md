---
title: "to dri or not to dri :-)"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by xander on 2005-01-28
Hi there.

What to do? Enable dri or disable dri. Comment this module in XFree86.conf?

My XFree86.0.log - part of it.
"
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "sisAGP" is not used
(==) RandR enabled
Symbol __glXActiveScreens from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXActiveScreens from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
"

What does it mean?

Thanks for help.
Xander

---

### Post by DJ_Max on 2005-01-28
DRI is direct rendering, and depending on your video card, it can be a good idea to enable it. Those errors don't look like a problem, especially if you experiance no issues.

---

