---
title: "Intel Shared Graphics no longer works after update to 9.10"
date: 2009-12-31
forum: Hardware
---

### Post by SingingBush on 2009-12-31
Since upgrading to Ubuntu 9.10 my laptop has been really slow.  It turns out it's due to Ubuntu not using the GPU.  

root@laptop-ubuntu:/home/mypc# **glxinfo | grep render**
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

root@laptop-ubuntu:/home/mypc#** egrep "(GLX|DRI)" /var/log/Xorg.0.log**
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(WW) intel(0): DRI2: failed to open drm device
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0

I have no idea how to fix this so please can someone let me know.

---

### Post by SingingBush on 2010-01-04
Any thoughts on this??   Anyone?

---

### Post by rshortt on 2010-01-09
I have the exact same problem.  Anyone?  I see there's no device under /dev/dri/ either, and the i915 kernel module is loaded, dmesg reports it loading.

---

### Post by rshortt on 2010-01-09
I think I fixed it.

I was using the kernel from 9.04, 2.6.28-11, and even though I had the package for 2.6.31-17 I didn't have it enabled in /boot/grub/menu.lst, so I just did that, rebooted, all seems fine now.

---

### Post by SingingBush on 2010-01-17
> **rshortt said:**
> I think I fixed it.

I was using the kernel from 9.04, 2.6.28-11, and even though I had the package for 2.6.31-17 I didn't have it enabled in /boot/grub/menu.lst, so I just did that, rebooted, all seems fine now.
Can you confirm if that worked or not and if so, run through the commands used to do all of that.

---

