---
title: "USB HD bricked?"
date: 2012-07-10
forum: Hardware
---

### Post by Langstracht on 2012-07-10
I just used ubuntu's Disk Utility to format a multi partitioned hard drive.

The "format" seemed to go "well" ... except I didn't see any lights flashing to indicate any disk activity.  Nonetheless I seemed to have ended up with an empty disk.

HOWEVER, it will NOT mount with ubuntu.

The log stops at "Attached SCSI disk".

I seemed to read that such not-mounting problems are not uncommon and the best (easiest?) way to fix 'em is by mounting the drive on a microsoft machine and doing chkdsk.  Fair enough.  A Windows machine (MS7 if it matters) gave a friendly beep when the HD was plugged in and, in a pop up, told me that the "new hardware" had been installed ... but it is nowhere to be found.

Anyone know how I can get over this?  I'd like my drive back.

TIA

---

### Post by wilee-nilee on 2012-07-10
I would try gparted, which from a Ubuntu install, needs to be installed to look at the HD, gparted can also be downloaded as a bootable disc as well, and is on the live Ubuntu cd.

 There are a number of partitioners that run in windows as well you can look on the web for them. Perfect disc the free download is one I often use to move all data to the front of the disc when doing windows partition size changes, it runs in windows and has some nice tools.

[http://www.raxco.com/](http://www.raxco.com/)

---

### Post by Langstracht on 2012-07-10
Thanks for taking the time to respond,

As far as I know I cannot use gparted if I can't mount the disk.  If gparted is usable with an unmounted disk please tell me how.

As for partitioning, in fact I do NOT want the disk to be partitioned.  Sorry for mentioning that it was before and, I guess, throwing you off track.

---

### Post by wilee-nilee on 2012-07-10
> **Langstracht said:**
> Thanks for taking the time to respond,

As far as I know I cannot use gparted if I can't mount the disk.  If gparted is usable with an unmounted disk please tell me how.

As for partitioning, in fact I do NOT want the disk to be partitioned.  Sorry for mentioning that it was before and, I guess, throwing you off track.

I suggested gparted and other partitioner’s as they may give you a clue as to why you are having problems.

---

### Post by ahallubuntu on 2012-07-10
To clarify, disks aren't "mounted" - only partitions are.  Gparted works with partitions on a disk, and it can simply be used to view the existing partition structure not change partitions.  It doesn't matter if there are any partitions on a disk or not - Gparted can still "see" it if registers as a drive.  If a partition is already mounted it will flag an error if you try to manipulate it.

Gparted is a useful, helpful tool to have on hand.

But instead of Gparted, try fdisk.  Open a terminal and type this:

```
sudo fdisk -l
```

and post the output of that here.

---

### Post by Langstracht on 2012-07-10
... but ... how do I get gparted (or any other utility) to access the drive?

---

### Post by Langstracht on 2012-07-10
Sorry, our messages sort of passed in the night there.

fdisk gives:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f55528b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1828    14683378+  27  Unknown
/dev/sda2   *        1829        1841      104422+   7  HPFS/NTFS
/dev/sda3            1842       21766   160046224    7  HPFS/NTFS
/dev/sda4           21766       38914   137736193    5  Extended
/dev/sda5           21766       38212   132100096   83  Linux
/dev/sda6           38212       38914     5635072   82  Linux swap / Solaris

Disk /dev/sdb: 8017 MB, 8017412096 bytes
186 heads, 43 sectors/track, 1957 cylinders
Units = cylinders of 7998 * 512 = 4094976 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        1958     7825408    b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table


Presumably my "problem" is /dev/sdc.  Sure hope you know what to do about it ...

---

