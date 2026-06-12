---
title: "Nikon Coolscan V (film scanner LS-50 ED)"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by dragonfly on 2005-02-19
Need some help getting this to work.
This is a dedicated film (not flatbed) scanner that is not automatically recognized.
dmesg | grep libusb gives me some output, manufacturer and product ID and what bus it is on.
Somehow I need to add that info to hotplug I guess. How?

Tx. :roll:

---

### Post by dragonfly on 2005-02-19
sane-find-scanner -->
found USB scanner (vendor=0x04b0 [Nikon], product=0x4001 [LS-50 ED]) at libusb:005:003


What next?

---

### Post by jamespi on 2006-01-24
your scanner is not supported by SANE


[http://www.sane-project.org/sane-mfgs.html#Z-NIKON](http://www.sane-project.org/sane-mfgs.html#Z-NIKON)

even though it finds and identifies scanners it doesnt necassarily support them.

---

