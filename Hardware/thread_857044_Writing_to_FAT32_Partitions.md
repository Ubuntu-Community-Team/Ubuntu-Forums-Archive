---
title: "Writing to FAT32 Partitions"
date: 2008-07-12
forum: Hardware
---

### Post by todd1049 on 2008-07-12
I installed ubuntu dual-boot with Windows Vista on my computer, with a FAT32 partition that (in theory) both OSes could read and write to.  However, ubuntu will not write to the FAT32 partition, even though it shows both the NTFS and FAT32 partitions as accessible from boot-up.  I thus assumed that it was mounting them automatically.  Is this a wrong assumption?  Will I have to tell it to mount the FAT32 before ubuntu will write to it?  If not, how can I fix this?  Many thanks!

---

### Post by matt$2 on 2008-07-12
The file /etc/fstab has the settings for setting the mode of mounting the partition.  i.e. Permissions for read write execute.

Post your fstab file and let's see what it says to adjust it accordingly.  It will only be a few lines long.

---

