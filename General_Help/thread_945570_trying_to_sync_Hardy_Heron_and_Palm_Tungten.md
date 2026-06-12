---
title: "trying to sync Hardy Heron and Palm Tungten"
date: 2008-10-12
forum: General Help
---

### Post by wendallsan on 2008-10-12
Hi all,

I've just inherited a Palm Tungsten (T1) after driving over my Lifedrive on accident, and am trying to get it to sync up with my Linux desktop so I can use Evolution to sync my calendar, etc.

I've found a few howto's on this but can't seem to get past one critical point on each of them.  No matter what I try, I can't get anything to show up at either /dev/pilot or /dev/ttyUSB*.  I've tried the howtos at these following pages:

[https://help.ubuntu.com/community/PortableDevices/PalmOS#Evolution%20and%20Gnome-pilot](https://help.ubuntu.com/community/PortableDevices/PalmOS#Evolution%20and%20Gnome-pilot)

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Again, no matter what I try, I'm just not getting anything to come up on either /dev/pilot or /dev/ttyUSB*, so I can't proceed with either of these howtos and get my syncing to work properly. I've already tried swapping USB cables and ports, and am using USB ports that work fine with other peripials.  If anyone knows any special voodoo on how to troubleshoot this step, I'd love to know about it.  Thanks for any help!

---

### Post by wendallsan on 2008-10-14
anyone?

---

### Post by openversus on 2009-01-26
Hi!
I had no problem to sync evolution and my Tungsten T until I used Hardy Heron.
Now I use Intrepid Ibex and I can't sync evolution with tungsten: when I try, it seems to be good ('cause the palm seems to work correctly), but in fact I have to real sync: if I change some data in evolution I don't find the changement in Tungsten T... so no sync :-)
I read a lot of webpages about this thread but no solution!

*my lsusb:*
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0830:0060 Palm, Inc. Tungsten C/E/T/T2/T3 / Zire 71
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

*my /etc/udev/rules.d/10-custom.rules file content's:*
BUS="usb", SYSFS{product}="Palm Tungsten T", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

In gpilotd I use ID:60 and /dev/ttyUSB0

Please help me\\:D/

Buena Vida!

---

### Post by kansas_plainsman on 2009-01-30
Apparently the specific kernel on which Hardy Heron runs is broken with respect to certain required libraries.  An update to a later kernel fixes it.  (Quick side note: if you are an nvidia user, you will have to reinstall the nvidia driver after the update).

---

