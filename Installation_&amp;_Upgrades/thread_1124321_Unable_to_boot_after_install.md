---
title: "Unable to boot after install"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by acocq on 2009-04-13
I installed 8.10 from the Live CD. It copied various files and then reboots the system.

I also have WinXP installed.

Instead of seeing any OS selection menu, I just see "GRUB" on the screen.

Here's the output from fdisk (running from LIVE CD) :

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
86 heads, 15 sectors/track, 757188 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      130056    83886112+   7  HPFS/NTFS
/dev/sda2          130057      757188   404500140    5  Extended
/dev/sda5          130057      325140   125829172+   7  HPFS/NTFS
/dev/sda6          325141      609638   183501202+   7  HPFS/NTFS
/dev/sda7          609639      757188    95169742+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcf5dcf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       60801   488376000    5  Extended
/dev/sdb5               2        1576    12651156    7  HPFS/NTFS
/dev/sdb6            1577        3919    18820116    7  HPFS/NTFS
/dev/sdb7            3920       60801   456904631    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg2   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       26888   215977828+   7  HPFS/NTFS
/dev/sdh2           26889       38913    96590812+   5  Extended
/dev/sdh5   *       33490       38913    43568248+  83  Linux
/dev/sdh6           26889       33213    50805499+  83  Linux
/dev/sdh7           33214       33489     2216938+  82  Linux swap / Solaris

Partition table entries are not in disk order

Any help would be sincerely appreciated !

Even just getting rid of GRUB (and back to WinXP) would be a great help.


Cheers,
Andreas

---

### Post by meierfra. on 2009-04-13
Try reinstalling grub from the LiveCD

```
sudo grub
```

and then at the grub prompt:

```

device (hd0) /dev/sdh
root (hd0,4)
setup (hd0)
quit
```

(this assume  that the  ubuntu "/" partition is /dev/sdh5. If its is /dev/sdh6, use "root (hd0,5)" instead.)

Reboot, but set the bios to boot from your 320 GB Ubuntu drive.

---

