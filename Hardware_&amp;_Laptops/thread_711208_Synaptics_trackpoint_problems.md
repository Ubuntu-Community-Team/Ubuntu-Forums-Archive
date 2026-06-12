---
title: "Synaptics trackpoint problems"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by dnquark on 2008-02-29
On a Fujitsu t2010 with a synaptics trackpoint, I can't get

1). tap-to-click behavior and
2). the sensitivity/acceleration settings seem to have little effect.

For thinkpads, it appears there is a tap-to-click setting in /sys/devices/platform/i8042/serio1/press_to_select, however press_to_select is not an option on my Fujitsu.  Please help me find drivers, or Xorg.conf incanctations to make this work.  Having a fully working pointing device is important to me.

---

### Post by dnquark on 2008-03-01
Replying to my own post: the fundamental problem here is that the hardware is not being detected as a touchpad, but instead as "PS/2 Generic Mouse".  This is *not* fixed in the current release of Hardy (Alpha 4).  I welcome any suggestions on how this could be fixed.

---

### Post by igknighted on 2008-03-10
> **dnquark said:**
> Replying to my own post: the fundamental problem here is that the hardware is not being detected as a touchpad, but instead as "PS/2 Generic Mouse".  This is *not* fixed in the current release of Hardy (Alpha 4).  I welcome any suggestions on how this could be fixed.

If you are still looking... you need to manually write a synaptics input device section in your xorg.conf.  Hopefully they will fix this soon...

---

### Post by dnquark on 2008-03-11
The xorg.conf has that section.  The problem is that the trackpoint is not detected as such by the kernel.  

Relevant lines from Xorg.0.log
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device

I submitted a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197905](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197905)

---

