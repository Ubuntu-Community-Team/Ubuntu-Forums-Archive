---
title: "strang df output, look!"
date: 2010-08-05
forum: Hardware
---

### Post by cnbiz850 on 2010-08-05
Just discovered:

```
$ df
File System           1K-block      used  available used% mount
/dev/sda1             14417392   3564992  10120036  27%   /
/dev/sda5             98046392   7734952  85330972   9%   /home

```

Look at sda5 for instance: 7734952 + 85330972 = 93065924 != 98046392

I thought the sum of used and available should equal (roughly) the total.  But in this case, 5GB is somehow missing.  Anyone tell me why is this.

---

### Post by cnbiz850 on 2010-08-08
Any thoughts?  Ideas?

---

### Post by Fafler on 2010-08-09
5 % of the disk space is reserved for root, in case the filesystem is full and the administrator needs to clean things up. 5% is quite a lot on modern PC's (it's always been like this, even when it reserved 2 mb of the first 40 mb drive i installed Linux on) and it's not really needed on /home. To fix it:

sudo tune2fs -m 0 /dev/sda5

---

### Post by cnbiz850 on 2010-08-10
> **Fafler said:**
> 5 % of the disk space is reserved for root, in case the filesystem is full and the administrator needs to clean things up. 5% is quite a lot on modern PC's (it's always been like this, even when it reserved 2 mb of the first 40 mb drive i installed Linux on) and it's not really needed on /home. To fix it:

sudo tune2fs -m 0 /dev/sda5

Thanks very much for the explanation.  That is very interesting.

---

