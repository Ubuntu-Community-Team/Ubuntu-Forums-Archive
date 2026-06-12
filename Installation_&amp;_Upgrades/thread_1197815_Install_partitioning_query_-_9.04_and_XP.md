---
title: "Install partitioning query - 9.04 and XP"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Red October on 2009-06-26
Hi there

First of all my sincere apologies if this duplicates an existing thread. I've looked at the forums and can't find a case that matches mine (i guess everyone is subtly different).

Anyway, i already have Win XP installed and wanted to install Ubuntu 9.04 alongside so i can dual-boot.

Minor issue. Although i know my pc has two 160GB hard-drives, windows sees c: as 296GB, so it appears that both hard-drives are viewed as one logical drive.

Main issue. When attempting the install i get to 'prepare disk space' screen and it says 'This computer has no operating systems on it'. The 'use the entire disk' option has two items in the drop-down - SCSI1 (0,0,0) (sda) - 160.0GB ATA Maxtor 6L160M0
and                               SCSI3 (0,0,0) (sda) - 160.0GB ATA Maxtor 6L160M0

After reading through some of the other postings i did sudo fdisk -l and this gave the following output

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       38436   308680942+   7  HPFS/NTFS
/dev/sda3           38437       38903     3751177+  db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

```Since i'm expecting the 'prepare disk space' screen to show me the Windows partition or at least some data already used i'm a bit nervous of continuing as i don't know what to expect.

I've got a Win XP OS backup and have backed up other critical data but i was hoping that i wouldn't be needing this.

Any advice that anyone can provide about how to carry on with the install would be most appreciated.

Thanks, RO.

---

### Post by merlinus on 2009-06-26
Are you  wanting to create space on your first hdd (sda) for ubuntu by shrinking the xp partition?  Or on sdb?  If the latter, then it has not been partitioned, as linux works with partitions and not simply hdds.

Whilst running from the live cd, you can open gparted (System/Administration/Partition Editor) and view your partitions that way.  And maybe post a screenshot.

---

### Post by Red October on 2009-06-26
Thanks Merlin

I'd already tried the gparted route but thought the fdisk output may be more useful. Anyway attached are the gparted screenshots (both disks).

RO

---

### Post by merlinus on 2009-06-26
Tres bizarro, since fdisk is showing partitions on sda.  You may wish to d/l and burn the .iso for gparted live, which is bootable and is a later version with more features than the one on the ubuntu cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by presence1960 on 2009-06-26
> **merlinus said:**
> Tres bizarro, since fdisk is showing partitions on sda.  You may wish to d/l and burn the .iso for gparted live, which is bootable and is a later version with more features than the one on the ubuntu cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

+1 
gparted live Cd is mucho better.

---

### Post by Red October on 2009-07-01
Thank-you for the advice. It appears i have some disk management software on my pc that's probably the cause of this issue. There's something called RAID0 Stripe which, apparently, means data is written to both 160Gb disks at the same time for larger files, thereby reducing the write time. I'm guessing that this is the cause of the issue. I will give the Gparted live option a go but i'm not too optimistic. Apparently i can opt to disable this feature but the result is that all data on the disks will be lost :???:

---

