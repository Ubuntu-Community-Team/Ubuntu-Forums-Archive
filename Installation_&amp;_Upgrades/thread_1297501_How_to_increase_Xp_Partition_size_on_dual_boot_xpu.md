---
title: "How to increase Xp Partition size on dual boot xp/ubuntu"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by chejesus on 2009-10-21
I have currently dual boot of Ubuntu 9.04 and XP.  I installed Ubuntu first and then XP.  I have a Toshiba Satellite L305D-S5868.  I have about 7 Gbs for XP and i want more (roughly 15-20) gigs.  Is there anyway I can increase the partition for XP or do i have to reinstall?  I tried to increase it using the Live CD and it only allowed me to shrink it and not increase it.

---

### Post by Mark Phelps on 2009-10-21
You do realize that you'll have to shrink Ubuntu first to make room for enlarging the XP partition, right?

Also, you would do better booting from a GParted LiveCD (which you can download from distrowatch.com) because, in order to shrink the Ubuntu partition, it must be unmounted -- and the LiveCD doesn't automatically mount any of the partitions.

---

### Post by raymondh on 2009-10-21
[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

-Back-up your files.  
-When using gparted, uncheck the "round to cylinder" box (something I learned from Herman and got to test recently).

Regards,

---

