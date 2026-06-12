---
title: "Intel GM45 graphics with 128Mb mode"
date: 2010-11-10
forum: Hardware
---

### Post by el_baby on 2010-11-10
Hi,

I'm testing an application running in the old Ubuntu 8.04.4 with a new motherboard. It's a customized installation without a desktop, I just launch X from a .profile file.

The motherboard is an [IEI NANO-GM45A2-R10]("http://www.ieiworld.com/product_groups/industrial/content.aspx?keyword=NANO-GM45A2&gid=00001000010000000001&cid=09050664803021477609&id=0A144509918722347516") (PDF user manual at [http://bit.ly/NANO-GM45A2_UMN_v1_00](http://bit.ly/NANO-GM45A2_UMN_v1_00)).

The BIOS has settings for the amount of memory it steals from the main memory for video: 32Mb, 64Mb and 128Mb.

I need all the memory I can get for video since the application blits a lot of large images to screen, however, if I set the BIOS to use 128Mb it shows garbage when I run xinit. Setting it to 64Mb works, but the performance of the application is sluggish (as compared to running on an older board: [Acrosser AR-B1892](http://www.acrosser.com/products/AR-B1892_detail_id_303.html)).

The older board has an Intel 945GM and is configured to steal 128Mb off the main RAM for video.

In both machines the xorg.conf file is pretty much the standard installed with X.org and they're both detected as 'intel'.

I've been browsing my Xorg.0.log files but can't figure out what's going on.

When X is wrong (using 128Mb for video ram and getting garbage in the screen), I see the following lines that don't appear when I use 64Mb and X displays OK:

```
+(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x800010bb to 0x8000085e
+(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00028283 to 0x00012d2d
+(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00014141 to 0x00009696

...

+(II) intel(0): fbc disabled on plane a
+(II) intel(0): fbc disabled on plane a
+(II) intel(0): fbc disabled on plane a
+(II) intel(0): fbc disabled on plane a
+(II) intel(0): xf86UnbindGARTMemory: unbind key 0
+(II) intel(0): xf86UnbindGARTMemory: unbind key 1
+(II) intel(0): xf86UnbindGARTMemory: unbind key 2
+(II) intel(0): xf86UnbindGARTMemory: unbind key 3
+(II) intel(0): xf86UnbindGARTMemory: unbind key 4
+(II) intel(0): [drm] removed 1 reserved context for kernel
+(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf89bd000 at 0xb728b000
+(II) intel(0): [drm] Closed DRM master.
+FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

Any help will be greatly appreciated.

---

### Post by el_baby on 2010-11-12
**bump** anyone?

---

