---
title: "IR printing"
date: 2008-09-08
forum: General Help
---

### Post by ikno0 on 2008-09-08
Hi,

I am trying to print via infrared, using a Sigmatel STIR4200 usb/infrared dongle... Ubuntu manages to see the dongle but it doesn't seem to give it any funtionality. I have installed the irda-utils as well.

I have done an "irdadump" but it does absolutely nothing.

I have done a "mknod irlpt0 c 161 16" and have tried to print directly to the printer with "cat FILE >/dev/irlpt0" but it tells me "permission denied", even after changing the permissions on irlpt0...

I would greatly appreciate any help on this subject...

Jason

---

