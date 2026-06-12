---
title: "Wrong detection of filesystem type - ext3 or ntfs"
date: 2008-06-11
forum: Hardware
---

### Post by volmark on 2008-06-11
I&#8217;ve installed second HD that was for formatted as NTFS with Windows 2003 on it.
Then I&#8217;ve formatted it with $ mkfs &#8211;t ext3 /dev/sdb1. Then it was  partitioned with sudo cfdisk. 
I could mount it and generally it works fine except when check this with sudo fdisk &#8211;l it still reports wrong file system: 

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

I have done it multiple times just to be sure that I done all the steps correctly but it still reports filesystem is HPFS/NTFS
Any suggestion???

---

### Post by logos34 on 2008-06-11
I believe the partition table was not updated when you formatted it ext3 with mkfs.

[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is one way to fix it.  Back up your data beforehand.

---

### Post by volmark on 2008-06-12
I’m quite newbie in Linux environment that’s why I need further instructions. 
What TestDisk version should I download, for kernel 2.4 or 2.6 ??
How I can find out what kernel vers. I run ??
How I can install TestDisk from …tar.bz2 ??
Is there more simple way to destroy NTFS partition tables and boot record on my second HD ?? Long time ago I’ve used low level utility for Windows where I could reset HD’s sectors manually bit by bit. Is there something similar for Linux ??

---

### Post by logos34 on 2008-06-12
sudo apt-get install testdisk 

sudo testdisk

is all you need to do.  

(I always run it from Parted Magic utility cd. It's now on the ubuntu live cd too I believe.  If not it can be installed like above)

that will allow you to fix the DOS type partition table, which is what the disk uses 

You might try deleting and creating partitions with Gparted--maybe that will edit the tables correctly where mkfs failed (but then again I think that's what it uses too, either that or mke2fs)

the dd command does a [low-level format]("http://wiki.linuxquestions.org/wiki/Blanking_a_hard_drive") (wipes the entire drive):

**sudo dd if=/dev/zero of=/dev/sdb conv=notrunc**

Be extremely careful with this command--get the drive letter right!

---

