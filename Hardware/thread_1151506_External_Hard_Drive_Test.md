---
title: "External Hard Drive Test?"
date: 2009-05-07
forum: Hardware
---

### Post by ToyotaGuy23 on 2009-05-07
I am suspicious about the integrity of my external hard drive.  

My rig:
Asus P5K-V
2.0 GB RAM
160 GB master / 250 GB slave / 320 GB usb external (all WD)
Ubuntu 8.10
Windows XP Pro (Dual Boot)

My problem:
This hard drive has always been kind of crappy.  One time I was moving some files from one drive to this one, and the power went out.  In windows, the file system went from being NTFS to 'RAW' and was unreadable.    

Never fear, I was able to save all of my data in Ubuntu to various other drives.  Now, I am ready to get this external drive usable again, and need some help.  

I installed gparted, and used that to make my file system FAT32.  Now when transferring files to the external usb drive, the "File Operation" seizes up and will not complete.  

I *BELIEVE* the problem may be a R/W access issue, but I'm not sure.  Neither Windows or Ubuntu likes this drive very much!  So, I would like to test it's integrity, and if it's acceptable, begin to use it again.  

HERE is what I have tried so far...
(forgive me, I am a bit of a newbie)

---
matt@matt-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2370

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32
---

and 

---
matt@matt-desktop:~$ sudo fsck /dev/sdb
[sudo] password for matt: 
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
---

Please help!  I really need to format my main hdd.  I need this usb external to backup my files.

---

