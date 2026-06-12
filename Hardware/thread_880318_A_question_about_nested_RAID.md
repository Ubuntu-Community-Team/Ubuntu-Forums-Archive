---
title: "A question about nested RAID"
date: 2008-08-04
forum: Hardware
---

### Post by neraph on 2008-08-04
I want to do some RAID benchmarks using Linux's software RAID, but I need some information before I invest in it.

First, I want to know if the software RAID supports arbitrary nested RAID configurations.  In other words, can I create a RAID array out of existing /dev/mdN devices?

For example, if I wanted to test RAID 5+0 using 6 drives, could I create two devices (/dev/md0 and /dev/md1) that are RAID 5 and then join them in a RAID 0 (on /dev/md2)?

Thanks,
Zach

---

### Post by tamoneya on 2008-08-04
since it is software raid you should be fine making 5+0.  The software only sees the devices not the actually hardware so it shouldnt really care.

---

