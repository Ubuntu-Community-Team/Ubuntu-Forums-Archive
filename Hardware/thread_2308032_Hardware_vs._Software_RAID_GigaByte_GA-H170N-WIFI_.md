---
title: "Hardware vs. Software RAID: GigaByte GA-H170N-WIFI vs. mdadm"
date: 2015-12-30
forum: Hardware
---

### Post by petwri on 2015-12-30
Easy question: I am about to get the Gigabyte GA-H170 MB, and I want to install a RAID5 containing 3x3TB. What would be a better option on Ubuntu 15.10: mdadm or the MB integrated RAID controller?

---

### Post by TheFu on 2015-12-31
Welcome to the forums.

I cannot think of **any** reason to ever use FakeRAID. Not one. Never.

FakeRAID has all the limitations/issues of HW RAID, without the speed. Why bother?
Look up "fakeraid issues" for more info.

---

### Post by SeijiSensei on 2015-12-31
I've used servers from Dell with PERC/SAS hardware RAID that works well with Linux since the driver is included in the kernel.  I looked briefly at the product description for the board you cited and can't see any mention of the RAID technology involved.  If it's indeed "fake" RAID as the TheFu mentions, which usually requires a Windows driver, then you should use mdadm.

---

### Post by petwri on 2016-01-29
Just to give you a little heads-up, I installed a RAID5 with mdadm, and on my Celeron 4400T, I hardly see any CPU usage, although the RAID is being accessed all the time. And it gives me all the fancy monitoring possibilities. So, my opinion is: mdadm is awesome, I can not see any reason to use anything else.

---

### Post by TheFu on 2016-01-29
> **petwri said:**
> Just to give you a little heads-up, I installed a RAID5 with mdadm, and on my Celeron 4400T, I hardly see any CPU usage, although the RAID is being accessed all the time. And it gives me all the fancy monitoring possibilities. So, my opinion is: mdadm is awesome, I can not see any reason to use anything else.

CPU is one thing. What about disk I/O performance?  bonnie++ is a tool for that. My RAID5 array was 3x slower than a single disk for writes, FYI. It is important to know the performance. For reads, it was 2x slower than a single disk. If that performance meets your requirements, great.

---

