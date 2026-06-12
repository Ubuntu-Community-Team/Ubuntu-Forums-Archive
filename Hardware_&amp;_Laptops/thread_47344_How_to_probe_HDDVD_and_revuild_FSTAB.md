---
title: "How to probe HD/DVD and revuild FSTAB"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by mc_cgp on 2005-07-08
Hi,

Justa add a new DVD Writer and HD to my Ubuntu box, how can I reprobe the Disks so that they get into FSTAB?

TIA

---

### Post by celloandy on 2005-07-08
Someone with a better understanding of the peculiarities of Ubuntu may be able to actually tell you how to automatically reprobe for your fstab entries, but frankly, it's not at all hard to do it by hand.  Adding this drive would only take one additional line to your current fstab, and it would be almost identical to the line already the optical drive that's already there.  All that would change is the mountpoint.  A quick Googling found [this](http://www.tuxfiles.org/linuxhelp/fstab.html) little explanation on how the file works.

Andrew

---

### Post by mc_cgp on 2005-07-13
[QUOTE=celloandy]Someone with a better understanding of the peculiarities of Ubuntu may be able to actually tell you how to automatically reprobe for your fstab entries, but frankly, it's not at all hard to do it by hand.  Adding this drive would only take one additional line to your current fstab, and it would be almost identical to the line already the optical drive that's already there.  All that would change is the mountpoint.  A quick Googling found [this](http://www.tuxfiles.org/linuxhelp/fstab.html) little explanation on how the file works.

Andrew[/QUOTE]

Hi,

would this be OK or must be rw

/dev/hdc        /media/dvdrw   udf,iso9660 ro,user,noauto  0       0

TIA

---

