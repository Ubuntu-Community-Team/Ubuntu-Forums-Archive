---
title: "I messed up my DRI"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by narnie on 2007-04-11
I was trying to compile some drivers for a mach64-based card on another laptop that failed so I thought I might compile the drivers on another laptop I have. I thought it would just make the modules (it didn't work, by the way).

the snapshots that I compiled redo the DRI for the mach64 card and are at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) (the common and mach64 drivers).

This reconfigured my DRI and whereas once glxinfo|grep "direct" told me yes, alas, due to my stupidity and newness to linux, mine now tells me:

direct rendering: No

how can I reconfigure my intel i915 card to DRI again. The driver is the i810 in xorg.conf

card info is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

lsmod |grep "drm"
drm                    74644  3 i915
agpgart                34888  3 drm,intel_agp

lsmod |grep "i915"
i915                   21632  2 
drm                    74644  3 i915

lsmod |grep "i810"
shows no output.

Thanks in advance.

---

