---
title: "bad sectors, how do i fix?"
date: 2010-03-26
forum: Hardware
---

### Post by REMIX8604 on 2010-03-26
i got my netbook today from dell.. with windows 7 so i instanly installed ubuntu remix 9.10 with wubi (dual booted) now my ubuntu it tells me i have 61 bad sectors. when i scan with windows it says no bad sectors. whats then mean? how do i fix it? thanks in advanced guys

also im sure you can tell... imma noob so be gentle with me =)

---

### Post by lindsay7 on 2010-03-26
Download any Ubuntu install disk of version 9.10 and burn it to a cd.  Run it without installing and open Gparted in the systems/administration menu.

click on the partition or drive you want to work on and click on "check" and run it.

You can also download Gparted from their web site and burn it to a disk which will start up your computer.  You can do the same check disk from there.

---

### Post by REMIX8604 on 2010-03-26
its weird.. both windows and linux are both on the same partition. i ran the iso in windows and ran wubi and clicked the "install thru windows"

anyways an update. right now i created a live usb ubuntu 9.10 and ran gparted clicked the check option for each partition. now it just says pending for each one. and isnt doing anything else...

still waiting 15 minutes later....

partitions:
fat16 DellUtility 40 mb
ntfs recovery 15 gb
ntfs OS 135 gb

---

### Post by lindsay7 on 2010-03-26
you have to click on the green check mark on the top menu.

When you have finished doing the file checking post the output of this command so we can see what is on your drive to verify what is going on here.

"sudo fdisk -l"     without the quotes and that is the lower case letter L not the number 1.

---

### Post by REMIX8604 on 2010-03-26
oops, i really should have thought to click the check mark, thanks. 
ok so i checked it and it gives me an error while checking the fat16 dellutility/40mb partition

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47ca95c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       19458   140888920    7  HPFS/NTFS

Disk /dev/sdb: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

---

### Post by lindsay7 on 2010-03-26
I do not see anything funny. It may be just how wubi see the dell partition.  You may want to start a new thread in the dell section of this forum asking about this.  FYI, a true dual boot is alot better and easier to trouble shoot in MHO.

---

### Post by REMIX8604 on 2010-03-26
ok, on to the dell threads =) thank you for you time in helpin me.

---

