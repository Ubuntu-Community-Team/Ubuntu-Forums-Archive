---
title: "gparted unallocated problem"
date: 2015-02-28
forum: Hardware
---

### Post by jgw on 2015-02-28
I have an 8gb flash drive.  I am trying to set it up as a boot drive so I can update my bios.  I am running with 14.10   Gparted tells me that the size is 7.52 gb, partition and file system are
 unallocated and used, unused are dashed.  The flash drive is not listed in my devices but gparted recognizes it (also lsusb).    I checked for errors and there are none.  

Here is the flash drive:
greg@greg-MS-7222:~$ sudo fdisk -l -u /dev/sdb
 
Disk /dev/sdb: 7.6 GiB, 8178892800 bytes, 15974400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x06608274

I have no idea how I cleverly did this.  I suspect it needs formatting but I can't get to it.  

Thank you...........

---

### Post by yancek on 2015-02-28
Use GParted to create a partition on it, either the entire drive or part of it, whichever you want.  Then format it.

---

