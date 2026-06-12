---
title: "Problem with partition"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Oskar_B on 2008-12-30
Hello,

I have recently downloaded Ubuntu, and I was hoping to install it. But the problem is that I cannot make a partition bigger than 8Mb, I have a Maxator 500Gb SATA-II HDD. When I go into the partition utility under Ubuntu I get this message relating my HDD: 

Anybody know how to fix this, because I really like this OS (Getting sick of XP) and I would really like to be able to use it without the CD.

(If this is posted in the wrong forum, I apologize)

Thank you.

---

### Post by davec64 on 2008-12-30
I'd do as it says!

Log into windows and run

```
chkdisk /f
```

That will hopefully sort all the errors on the partition.

All the best:D

---

