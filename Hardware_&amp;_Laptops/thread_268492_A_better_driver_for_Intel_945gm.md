---
title: "A better driver for Intel 945gm?"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by Faytz on 2006-09-30
Is there a better driver than i810 for 945GM?
Whenever i did cat /var/log/Xorg.0.log | grep dri it says:
 X.Org XInput driver : 0.5
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
ABI class: X.Org XInput driver, version 0.5
ABI class: X.Org XInput driver, version 0.5
ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [dri] visual configs initialized 

But then when i check the xorg.conf it still says i810 for the gfx driver.Why is that?

---

### Post by tsberry901 on 2006-10-19
Check out the Intel web site. They have the driver for linux now.

---

### Post by SonicTheHedgehog on 2006-11-15
> **tsberry901 said:**
> Check out the Intel web site. They have the driver for linux now.

How do I install the driver?

---

### Post by alinuxfan on 2006-11-15
check out [this post]("http://ubuntuforums.org/showthread.php?t=281275") in the forums
It should guide you right through it

---

