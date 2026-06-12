---
title: "Scanner not recognised"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Pete051 on 2006-06-12
I see a few other people have this problem but as yet no answers so I'll try and hope someone has found a solution :) My scanner an old trust jobby used to work fine with breezy but is apparently invisable with dapper. well not really, xsane appears and disappears to fast to read what it's problem is and kooka just asks if I want to use the scanner and then tells  me it can't find it.
sane-find-scanner gives me "found USB scanner (vendor=0x055f, product=0x0006, chip=MA-1017) at libusb:001:003
found USB scanner (vendor=0x06b9, product=0x4061) at libusb:001:004"
scanimage -L gives me : "device `mustek_usb:libusb:001:003' is a Mustek 1200 UB flatbed scanner"
lsusb gives me :  Bus 001 Device 003: ID 055f:0006 Mustek Systems, Inc. ScanExpress 1200 UB

All of the above is as normal (not root) user so the scanner is being recognised and the problem isn't with permissions. but what the problem is I've no idea any offer?
Thanks
Pete

---

### Post by alienexplorers on 2007-02-06
Did you select in snyaptic sane, xsane, libsane, and libsane-extras.

---

