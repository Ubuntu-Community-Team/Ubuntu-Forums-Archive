---
title: "External Hard Drive won't mount"
date: 2010-07-28
forum: Hardware
---

### Post by alas-poor-yorick on 2010-07-28
I have a 320 GB LaCie external hard drive that won't mount on any OS (Windows XP/Vista, Ubuntu Lucid, or Mac OSX), and I'm hoping it's a problem with the MBR/partition table so I can restore it without losing data. When I plug it into Ubuntu, I get:
```
Unable to mount LaCie
Error mounting: mount exited with exit code 2:
```
GParted shows one giant NTFS partition, while testdisk 6.11, Acronis for Windows, and a Windows boot cd all show a large NTFS partition with a bit of unpartitioned space at the end of the drive. I'm not sure what this means about the partition table. Interestingly, testdisk 6.12 doesn't recognize the drive at all.

here's fdisk -l:
```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x454c0bc6

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
```

And ntfsfix:
```
$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
```
```
$ sudo ntfsfix /dev/sdb1
Mounting volume... Segmentation fault
```

When I plug it into Windows, it shows the filesystem as RAW and 0 bytes used, 0 bytes available.

On both Linux and Windows, testdisk exits with the error message "Segmentation fault" when attempting various things.

Any ideas for what is wrong, and how to fix it?

Thanks.

---

### Post by jmickela on 2010-09-02
Did you ever get a fix for this?

I'm having exactly the same issue:
USB drive died, trying to use ntfsfix, but it's crashing.

I love the irony that the tool I'm trying to use to fix my drive itself seems to need to be fixed.

---

