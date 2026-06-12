---
title: "[SOLVED] Installed 8.04 Now Need To Remove Windows"
date: 2008-08-04
forum: General Help
---

### Post by terry123b99 on 2008-08-04
Ok quite new to this although have used older versions of Ubuntu. Basically I installed Ubuntu via Windows using the included installer, am sure I only allocated Ubuntu 15GB and need to increase this. I would like to remove the Windows XP partition and have Ubuntu soley running on my laptop.

My current partitions look like this
> 
terry@terry-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb58e199

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       15854   127339222+   f  W95 Ext'd (LBA)
/dev/sda2   *       15855       29978   113446912    7  HPFS/NTFS
/dev/sda3           29979       30400     3389715    7  HPFS/NTFS
/dev/sda5               2       15854   127339191    7  HPFS/NTFS


My question is really, how do I merge my partitions together so they are one huge Ubuntu one without affecting or damaging my current Ubuntu installation.

Thanks in advance :)

---

### Post by Elfy on 2008-08-04
I think you need to look at lvpm

[https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by philinux on 2008-08-04
If you used wubi to install then I suggest you get Ubuntu live cd and install it normally. This will format the drive in the process.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn the iso file at 4x speed as an image.

---

### Post by northern lights on 2008-08-04
You used "Wubi"?

Anyway, you have not installed Ubuntu as a standalone operating system yet. Or posted not the entire 'fdisk' output. Your partition table has got not a single Linux entry.

If you're sure you want to drop Windows, backup your personal data, pop the LiveCD in and install.

A 10 gig partiton for Ubuntu itself will suffice, if you create a separate /home.

---

### Post by terry123b99 on 2008-08-04
thanks for the replies, have decided to re-install the whole OS as a standalone and not dual boot with any versions of Windows. Took a few hours to re-install my programs but worth it, as it runs a lot faster now.

Cheers :)

---

### Post by JoshuaRL on 2008-08-04
> **terry123b99 said:**
> thanks for the replies, have decided to re-install the whole OS as a standalone and not dual boot with any versions of Windows. Took a few hours to re-install my programs but worth it, as it runs a lot faster now.

Cheers :)

Make sure you thank those that helped you, and look in Thread Tools at the top to mark as solved.

And welcome to Ubuntu, For Real This Time (R)

:lolflag:

---

