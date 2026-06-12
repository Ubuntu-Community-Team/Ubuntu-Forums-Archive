---
title: "Long reboot time - 7.10 - Acer Aspire 5100"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Jay_Davis on 2007-10-30
My Acer Aspire 5100 with Ubuntu 7.10 (fully updated) takes about 3 1/2 minutes from clicking restart to getting to login screen. This seems way too long to me, XP boots in less than 30s. Since this is a laptop it's important that I can it on and off quickly. Specs are:

AMD Turion64 2.0Ghz
1GB RAM
ATI Xpress 1100 (200m) Integrated Graphics (Not using restricted drivers)
Broadcom Wireless (Not using restricted drivers - not using any actually, it's not supported)

I repeated it three time, all were within 5 seconds of 3:30 so it's a consistent and repeatable bug. Any ideas on how to fix this?

---

### Post by cymacyma on 2007-10-30
read this!

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)

It maybe help you '&#12613;'

---

### Post by Jay_Davis on 2007-11-02
OK so the bug seems to be a problem with the resolution of the boot splash screen. It's not being properly detected and set, so I had to edit the file /etc/usplash.conf and set the right resolution (1280x800). Thanks for pointing me in the right direction.

---

