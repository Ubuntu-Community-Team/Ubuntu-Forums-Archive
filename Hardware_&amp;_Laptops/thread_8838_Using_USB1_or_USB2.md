---
title: "Using USB1 or USB2 ???"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by ghetto on 2004-12-21
How to know if a device is using USB1 or USB2 ?
I have a 1GB USB pen (compatible with USB1 & 2) and it seems really slow to transfer data...

---

### Post by diebels on 2004-12-28
is "ehci-hcd" loaded?

---

### Post by hardcandy on 2004-12-28
Is the device "fullspeed" or "highspeed" USB 2?
From usb.org: 
Q1: How fast is USB?
A1: High speed USB products have a design data rate of 480 Mb/s. Full speed USB devices signal at 12Mb/s, while low speed devices use a 1.5Mb/s subchannel.


Basically a ripoff, when the usb.org came out with the USB2 specs, a bunch of manufacturers had a lot of older USB chips in inventory. So they made two USB2 specifications. And the manufactureres could call their 12 Mb/s devices "USB2" on the packaging. They just have to indicate somewhere if it is Fullspeed or Highspeed USB2.  USB 1 devices are the 1.5 Mb/s.

---

