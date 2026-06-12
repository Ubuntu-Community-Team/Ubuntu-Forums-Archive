---
title: "Averatec 2150 (MSI s270 MS-1013) hibernate issue"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by maliath on 2007-10-20
I have an Averatec 2150 laptop. Hibernate does not work. Does anyone have any suggestions? My video card is an ATI 200m

---

### Post by balak on 2007-10-22
Look at this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

There are some suggestions there.
Basically you can either have 3D acceleration (ATI restricted driver fglrx) or suspend/hibernate but not both till a fix is found for this.

I am ASSUMING you have Gutsy 7.10. 

I have been able to suspend/hibernate in feisty w/o any issues.

---

