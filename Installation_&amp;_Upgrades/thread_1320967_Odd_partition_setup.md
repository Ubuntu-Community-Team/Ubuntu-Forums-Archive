---
title: "Odd partition setup?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by GimmeCoffe on 2009-11-09
All right, I have another Dell computer with one SATA drive, and I am trying to dual boot with Wubi.  The drive mode is set to ATA, because of XP.  However, the partition setup is unusual.


[LIST]
[*]C: is a data partition. Originally, it was a Vista Partition, but is corrupted.
[*]D: is my operating system, which is windows XP.
[*]E: is the Dell recovery drive.
[*]There is also a blank 39MB partition, probably partition info.\
[/LIST]
However, C: and E: are primary, and my D: (OS partition) is logical drive.  Will this cause any problems with Wubi?

---

### Post by darkod on 2009-11-09
As far as I know, wubi just "installs" ubuntu like a software in windows. It doesn't do any partitioning so it would't fail just because partitions.

But it does need 5GB minimum free space on any drive. When you start wubi it will ask you on which drive you want the 5GB (or more, you can choose, not sure about less) to be reserved. It will add an entry in the windows boot loader and that's it.

Don't forget, it is something like a virtual box, nothing more. Not sure you should do any serious work in it, but for testing around looks fine. Then you just de-install it like any windows software, in remove programs.

---

### Post by GimmeCoffe on 2009-11-09
All right, but now it gives me an error, no root filesystem defined. I am guessing the problem is the mount point that wubi set, however I don't know how to access the settings from windows. any

---

### Post by wilee-nilee on 2009-11-09
> **GimmeCoffe said:**
> All right, but now it gives me an error, no root filesystem defined. I am guessing the problem is the mount point that wubi set, however I don't know how to access the settings from windows. any

You have to install with wubi from administrative I believe, are you doing this?

---

### Post by GimmeCoffe on 2009-11-09
Yep.

---

### Post by wilee-nilee on 2009-11-09
If you can post a screen shot showing the partitions it would probably be helpful. Letters for partitions from the Linux side are not really applicable for analysis, unless your a knowledgeable windows user. 

Also any licensed previous OS of W7 can get a upgrade for cheap if your a student at a college you may get it for free or 29$ you might consider this option.

---

### Post by GimmeCoffe on 2009-11-18
I have the Win7 cd, but I prefer XP.  It seems faster than 7 and Vista.

---

