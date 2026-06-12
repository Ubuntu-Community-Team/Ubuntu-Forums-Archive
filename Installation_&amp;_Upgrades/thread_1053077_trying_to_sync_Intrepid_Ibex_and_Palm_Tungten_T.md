---
title: "trying to sync Intrepid Ibex and Palm Tungten T"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by openversus on 2009-01-28
Hi!
I had no problem to sync evolution and my Tungsten T until I used Hardy Heron.
Now I use Intrepid Ibex and I can't sync evolution with tungsten: when I try, it seems to be good ('cause the palm seems to work correctly), but in fact I have not a real sync: if I change some data in evolution I don't find the changement in Tungsten T... so no sync :(
I read a lot of webpages* about this thread but no solution!

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
_____________________
* like these:
[https://help.ubuntu.com/community/PortableDevices/PalmOS#Evolution%20and%20Gnome-pilot](https://help.ubuntu.com/community/PortableDevices/PalmOS#Evolution%20and%20Gnome-pilot)

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

### Post by openversus on 2009-02-04
Simple solution...
I finally sync my Tungsten T with evolution with ubuntu (studio) 8.10: I use **Multisync-gui**.
I hope this info will be useful to someone :-)
Buena vida..

---

