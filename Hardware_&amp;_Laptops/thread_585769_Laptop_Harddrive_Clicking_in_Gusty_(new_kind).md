---
title: "Laptop Harddrive Clicking in Gusty (new kind)"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by leptons on 2007-10-21
I know that previously there was this bug that SATA laptop harddrives keep clicking once in a while...


that was fixed by doing
sudo hdparm -B 255 /dev/sda

even in beta Gusty, things were fine.

However, I noticed that after I installed the new Gusty, a new kind of clicking appears. It is not as loud as the old kind of click. Actually, it's not really clicking, it sounds like something is spinning and then gets stuck for a bit.. then it spins again. I tried the hdparm fix but this time it doesn't work.

I have a MSI 1220 (specs pretty much same as Darter Ultra 2)
and a WD Scorpio SATA 160 HD.

Is anybody else having the same issue?

---

### Post by Linicks on 2007-10-22
Try mounting the partition with the 'noatime' attribute.  Instructions here:

[http://ubuntuforums.org/showthread.php?t=584790](http://ubuntuforums.org/showthread.php?t=584790)

Nick

---

