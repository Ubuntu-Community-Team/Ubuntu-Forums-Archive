---
title: "Configuration problem with elentech touchpad"
date: 2011-06-12
forum: Hardware
---

### Post by Helios747 on 2011-06-12
Hello,

I'm running Natty 64 bit on an ASUS n53e which has an elentech touchpad.

The touchpad functions well enough, but I wanted to disable tap to click. However in the Mouse preferences there's no touchpad tab.

After a bit of googling, it seems that my touchpad is being picked up as a logitech PS/2 wheel mouse, which Synaptics doesn't support.

The weird thing is that apparently the patch for it was fixed in 2.6.36. However I'm running 2.6.39.1 (made sure the elentech config option was checked in the PS/2 section) and I'm still getting no configuration options in Mouse preferences. The touchpad is still being detected as logitech

```
I: Bus=0011 Vendor=0002 Product=0001 Version=0063
N: Name="PS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
```

I've tried synclient to disable tap to click, however it just complains about synaptics not being loaded. I also don't have an xorg file (just using the defaults, which means no xorg file)



I thought this was supposed to be fixed! D:

help!

---

### Post by Helios747 on 2011-06-19
bump

---

### Post by Helios747 on 2011-06-19
found a fix.   

Follow these instructions, may work on other ASUS laptops.   

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192/comments/95](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192/comments/95)

---

