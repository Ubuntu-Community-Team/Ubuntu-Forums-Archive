---
title: "ASUS A7V8X-X doesn't mount UMS device"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by parabolize on 2005-07-16
My iriver MP3 Player (Model: IFP-890) does not work with my ASUS A7V8X-X motherboard. The MP3 Player has the UMS v1.28 firmware on it and works just fine with my old Compaq that is also running Ubuntu 5.04. I have a USB mouse that works OK in the ASUS motherboard. Here is what I get with dmesg:
```
dmesg | tail
agpgart: Xorg passes broken AGP3 flags (1f00000c). Fixed.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
eth0: no IPv6 routers present
usb 4-5: new high speed USB device using ehci_hcd and address 3
usb 4-5: device descriptor read/64, error -71
usb 4-5: device descriptor read/64, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 4
usb 4-5: device descriptor read/64, error -71
usb 4-5: device descriptor read/64, error -71
``` 

Whats going on? Why would a mouse work but a UMS device not?

---

