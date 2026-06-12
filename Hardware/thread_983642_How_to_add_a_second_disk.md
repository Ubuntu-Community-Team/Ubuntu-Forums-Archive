---
title: "How to add a second disk"
date: 2008-11-15
forum: Hardware
---

### Post by bachurch on 2008-11-15
I have a old Dell P3, 500Mhz, 1/2 Gig ram.
I have a 30 gig drive and cd-rw on the primary ide and a 120 gig drive on the secondary ide. How do I get the system to recognize the second disk, setup etc. I want top use this primarily as storage server plus have fun getting to know Ubuntu.
I am sure this is documented somewhere but I have not found it yet.

btw I can see the second drive in bios setup
Thanks,
Brian

---

### Post by Marcus Derekus on 2008-11-15
Is Ubuntu not reading the drive or something?

in Ubuntu open up places/computer and see if you drive is under file system on the side bar

---

### Post by taurus on 2008-11-15
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
```
To use the second harddrive, you need to format it and then add an entry in /etc/fstab so it would be mounted automatically each time you boot.

---

### Post by bachurch on 2008-11-16
I have cdrom and floppy.

---

### Post by bachurch on 2008-11-16
> **taurus said:**
> Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
```
To use the second harddrive, you need to format it and then add an entry in /etc/fstab so it would be mounted automatically each time you boot.

I want to format the drive but I can't get to it.
Here is the output.

brian@bdiubuntu:~$ sudo fdisk -l
[sudo] password for brian: 

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaddaadda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris
brian@bdiubuntu:~$ sudo blkid
/dev/sda1: UUID="22221587-8402-4fa8-8183-d8ef5fc69991" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5ebd26e9-95a5-45f0-8d4a-b2a4baf6cb3d" 
brian@bdiubuntu:~$

---

