---
title: "Kernel Module load order"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by floe-de on 2006-12-24
Hi,

my problem is that I have a analog tv-card (bttv module) AND a digital tv-card (ivtv module)
on every boot I don't know which one loads first so one time the analog card has /dev/video0
and another time the digital card has this device.

I can change this by hand -> unload both modules and load it in the right order, but that's not the best solution.

So my question is:
How can I load kernel modules in a specific order ?

Thanks
Flo

---

### Post by po0f on 2006-12-24
floe-de,

You'd be better off writing custom udev rules to handle all the /dev entries for you.  [Link](http://www.ubuntuforums.org/showthread.php?t=168221) to get you started (it's about removable devices, but the process is almost the same).

---

