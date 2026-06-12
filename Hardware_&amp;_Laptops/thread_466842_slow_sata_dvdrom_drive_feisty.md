---
title: "slow sata dvdrom drive feisty"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by finite9 on 2007-06-07
Running feisty on HP Pavilion dv9297ea with SATA DVD multi drive and SATA hard drives.

Performance sucks.  DMA is mandatory in SATA standard, so thats ok.  hdparm does not wotk on SATA drives, and sdparm cannot tune performance parameters of drives.

Is there a bug in sata driver in linux kernel included with feisty?

I have Intel ICH7 chipset and I vaguely remember there being issues with this chipset in 2.6.20.  Is this the reason for slow performance?

I get about 48MB/s with hdparm -Tt on the hard drive which is pretty good I guess...twice as fast as PATA drive in old laptop, but same test on DVD drive gives 1MB/s!!

DVD movies do not stutter, but read/write performance is really bad.  Does anyone have any ideas how to fix this or if it can be fixed?

---

