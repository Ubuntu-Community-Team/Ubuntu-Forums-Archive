---
title: "DVD Player-wrong disc permissions"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by Uta on 2006-08-01
I am using the latest PPC version of Dapper on an Old World Mac. I have two DVD players, one internal via IDE/PCI and one external via a FW box. The external views an inserted disc as belonging to "my username" or undetermined whereas my internal DVD player views an inserted disc as belonging to root or on some discs as undetermined. I can play a DVD movie via the external DVD player but not with the internal due to the permissions issue.

The internal DVD drive is listed in my FSTAB as:
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0

This command gets me this (the dvd player is on hde)
 ls -la /dev/hde

brw-rw---- 1 root cdrom 33, 0 2006-08-01 16:22 /dev/hde


How do I fix this permission issue. Thanks!

---

