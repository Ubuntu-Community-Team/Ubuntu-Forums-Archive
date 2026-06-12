---
title: "[SOLVED] really quick Graphics card question"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by uberlube on 2008-03-09
I just installed Mint on my friends sons new HP pavillion dv9000 laptop and was pleasantly surprised that the wireless worked out of the box. One less this I have to set up. My question is that this laptop uses an Intel(R) 965 Express Chipset Family graphics card. Do I actually need to install a driver in this? Does it work off the nvidia driver or do I need to grab something else?

---

### Post by ShodanjoDM on 2008-03-09
```
aptitude show xserver-xorg-video-intel
```

```
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
```

I think it's installed by default.

---

### Post by acron1 on 2008-03-09
No you should be OK out of the box:)

---

### Post by uberlube on 2008-03-09
```
$ aptitude show xserver-xorg-video-intel
Package: xserver-xorg-video-intel
State: installed
Automatically installed: no
Version: 2:2.1.1-0ubuntu9
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 487k
Depends: libc6 (>= 2.6-1), libdrm2 (>= 2.3.0), xserver-xorg-core (>= 2:1.3.0.0)
Conflicts: xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-video-i810-modesetting,
          xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-1.0
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips.

 This package also provides an XvMC (XVideo Motion Compensation) driver for the
 same chipsets.

 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

 This package is built from the X.org xf86-video-intel driver module.

```

This is what i get

---

### Post by ShodanjoDM on 2008-03-09
Well it says that it's installed

> Package: xserver-xorg-video-intel
State: installed


So I think you're good to go :guitar:

Try enabling compiz, or better yet, check with glxgears first.

```
$glxgears -info
```

---

### Post by uberlube on 2008-03-09
K Im good to go, just wanted a second opinion before I enabled compiz and messed up X all together. I sent my thanks :)

---

### Post by ShodanjoDM on 2008-03-09
You're welcome, glad I can help :D

---

### Post by acron1 on 2008-03-09
Thanks,
Steve

---

