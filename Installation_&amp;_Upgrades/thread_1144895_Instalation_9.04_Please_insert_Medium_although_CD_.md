---
title: "Instalation 9.04: Please insert Medium although CD is inside"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by haaees on 2009-05-01
During the Instalation of 9.04 I get the following message at 75% of the base-system-instalation:

```
Please insert the medium labeled Ubuntu 9.04 _Jaunty Jackalope_- Release i386 (20090420.1)' in the drive /cdrom/ and to press Enter.
```The CD is already in the drive, so I can't proceed with the instalation.

---

### Post by NilsE on 2009-05-01
Assuming you have hit enter and it still hangs you may have a bad CD.  Try reburning the CD at a slower burn rate and try again.

---

### Post by haaees on 2009-05-01
I checked the CD, everything is OK.

At another PC the instalation with the same CD was no problem.

I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/351053](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/351053)

In the last post, there is a workaround. But this only follows to many other error reports.

---

