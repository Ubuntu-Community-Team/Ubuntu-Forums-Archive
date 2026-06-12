---
title: "firewire device not working correctly"
date: 2009-05-21
forum: Hardware
---

### Post by Silmaril89 on 2009-05-21
Hi,

I'm trying to use my 3rd generation ipod with ubuntu, but when I plug it in, it is unable to be mounted.  As soon as it is attached, it begins charging, and dmesg displays the following:

> [88373.767188] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0

I have tried all of the following modules:

raw1394
ieee1394
ohci1394
eth1394

and a few others.

running sudo fdisk -l does not list my ipod.

Also, my ipod does mount correctly with a usb cable, but the battery on my ipod does not last long enough to be able to really do much with it(I've had it for quite sometime now), and this specific ipod only gets power over firewire and not usb.  About 15% of the time that I plug my ipod into firewire it does in fact mount, but never stays mounted for more than a few minutes.  It also mounts fine while in windows(but I'm using a different machine all together to test this).

I've seen a few threads about this on the internet and on this site, but I haven't seen one that has been solved yet.  

Please help.

---

