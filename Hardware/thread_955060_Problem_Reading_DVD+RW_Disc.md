---
title: "Problem Reading DVD+RW Disc"
date: 2008-10-21
forum: Hardware
---

### Post by xp_newbie on 2008-10-21
I have a DVD+RW disc that was created on Fedora Core 4, using cdrecord:
```
cdrecord -v -sao speed=4
```
I have no problem reading it on a laptop running Windows XP SP2.

But the same exact disc, under Ubuntu 8.04 (ASUS DRW-2014L1T drive) cannot be read.

I know that the ASUS DRW-2014L1T drive is fine because it was used to install Ubuntu 8.04 itself...

Any idea what could be the problem (and how to fix it)?

Thanks,
Alex

---

### Post by amauk on 2008-10-21
Is Ubuntu on the same laptop (that successfully read the disk under XP)?

reason I ask, is you need a rewritable drive in order to read rewritable disks

---

### Post by xp_newbie on 2008-10-21
No, the Ubuntu 8.04 that is unable to read the DVD+RW is not on the same latpop. It is on a desktop machine. However, its drive ***is*** a rewritable drive (ASUS DRW-2014L1T)

To make this clearer:
[LIST=1]
[*]The DVD+RW disc is burned on machine A (Fedorca Core 4).
[*]The DVD+RW disc can be read on a laptop B (Windows XP SP2)
[*]The DVD+RW disc cannot be read on machine C (Ubuntu 8.04)
[/LIST]

I suspect the problem has to do with the switches used in cdrecord (or the disc type, i.e. +RW vs. -RW), but I am no expert on this. I would appreciate some guidance or tips that will help me solve this problem.

Thanks,
Alex

---

### Post by amauk on 2008-10-21
well, only thing I can suggest, is read in XP, copy contents off, re-burn (possibly to DVD-R, just to eliminate any RW problems)

---

### Post by xp_newbie on 2008-10-21
Thanks for your suggestion but I am not looking for how to save this particular disc contents. I can read it on at least 2 machines.

What I am looking for is a permanent solution to this ASUS drive problem with Ubuntu 8.04. It is brand new. I just burnt a CD using this drive from the same Ubuntu. I know it's only a configuration problem. I am looking for the "magic trick" :)

---

