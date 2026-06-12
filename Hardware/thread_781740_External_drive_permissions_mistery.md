---
title: "External drive permissions mistery"
date: 2008-05-04
forum: Hardware
---

### Post by Uncle Joe on 2008-05-04
I got myself the external hard drive today - 750GB WD "My Book". Reformatting it to Ext3 (I don't need Windows compatibility anyway) went fine but after that some troubles occured. The owner of the drive appeared to be root and 'chmod -R myusername:users /dev/sdb1' did not help it.

Any ideas why could it be and where to dig now?

Here's the fstab line: 
/dev/sdb1 /media/My\040Book ext3 users,atime,auto,rw,nodev,noexec,nosuid 0 0

P.S. To add further confusion, the fdisk -l shows the following:

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    c  W95 FAT32 (LBA)


See FAT32 there? Is it supposed to be this way?

---

