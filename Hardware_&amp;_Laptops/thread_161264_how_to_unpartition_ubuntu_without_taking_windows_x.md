---
title: "how to unpartition ubuntu without taking windows xp off?"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by jgirl57 on 2006-04-16
hello,
 i have a vaio fs760 and i was wondering if someone new how i could take ubuntu off my computer with out taking off windows xp because i dont have the  back up cd

---

### Post by aysiu on 2006-04-16
You'll need some kind of Windows CD if Ubuntu's Grub is installed to the MBR. The main issue is that you want Windows to take back the Master Boot Record. Once you do that, taking the Ubuntu partition off is as easy as going to Disk Management in the Control Panel of Windows and reformatting it as NTFS or FAT32.

---

### Post by teasum on 2006-04-16
From your post I assume you have XP and Ubuntu both installed as a dual-boot system, and that you want to go back to a single partition with XP as the OS.  Assuming that the XP partition is the first one on the drive, and that you don't have data you need to save on any other partitions, the simplest option without deleting XP is to use a partition editor (such as a Gparted LiveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) to wipe out all Linux partitions and expand your XP partition to cover the entire hard drive.

Depending on how you installed Ubuntu, you'll probably have to repair your Master Boot Record (MBR) in order to allow XP to boot.  To do this, the easiets thing to do would be to borrow a friends XP install CD (which you say you don't have), enter the recovery console, and enter the command "FIXMBR".  In the absence of an XP CD, there are other tools out there (Live CDs, bootdisks, etc.) that can do this for you, but I'm not 100% sure which would work best in your case.

---

### Post by teasum on 2006-04-16
Update: Here are links to two free utilities that purport to repair the MBR from within XP:
Super Fdisk
[http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/Super_Fdisk.html](http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/Super_Fdisk.html)

HDHacker
[http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/HDHacker.html](http://www.freedownloadscenter.com/Utilities/Disk_Maintenance_and_Repair_Utilities/HDHacker.html)


If these work (and I've never tried them), then you could repair the MBR first, then simply repartition the hard drive as mentioned above.  It looks like Super Fdisk works as a graphical partition manager as well, but you'll have to partition from a live CD or boot disk, so I still recommend Gparted Live CD (or the Ubuntu Live CD, which has Gparted installed).  

Good luck, but I hope you consider Ubuntu again in the future.

---

