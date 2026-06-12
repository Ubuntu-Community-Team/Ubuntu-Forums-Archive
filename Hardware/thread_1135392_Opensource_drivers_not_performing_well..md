---
title: "Opensource drivers not performing well."
date: 2009-04-24
forum: Hardware
---

### Post by dE_logics on 2009-04-24
Apart from installing the driver rapper and radon prebuilt packages, I also installed the radionHD package...installing this package eluded some issues.

But still there're lots of issues left, for instance the graphs performance is about 1/5 th of what it was with windows so k-3d, blenders and games working with WINE work very slow.

In k-3d I cannot select objects.

I tried to compile to sourcecodes of the HD drivers for optimal performance (after removing the installed binary packages) reading [this]("https://help.ubuntu.com/community/RadeonHD"), but it asked to configure the xorg.conf file; in the configuration I've noticed on including this section under the device category - 

```

Driver   "radeonhd"

```

Almost all sorts of rendering stops; that includes videos, desktop effects, and ofcourse 3-d applications (k-3d and blenders) and the simple 2-d GUI becomes extremely slow and buggy.

On removal of that line things start working better, but I have to reinstall the ATI driver wrappers + radon drivers + HD drivers to get back that performance before the modification.



So finally what I'm asking here, is how to configure that xorg file properly?...cause what's given in that tutorial is not working.

---

### Post by dE_logics on 2009-04-25
No one knows?

---

### Post by dE_logics on 2009-04-26
If I keep refreshing this thread maybe **someday** I'll get a solution.

---

