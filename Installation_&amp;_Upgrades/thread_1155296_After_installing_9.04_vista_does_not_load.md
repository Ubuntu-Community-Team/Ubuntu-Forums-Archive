---
title: "After installing 9.04 vista does not load"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by skykaptain on 2009-05-10
Hello,

I installed Ubuntu 9.04 on a HHD that contains XP and now Ubuntu but I also have a HHD with Vista on it. The Vista HHD had the bootloader for when I just had XP and Vista. When Grub comes up and I select Vista nothing happens, the screen just says, "Starting up...."

Here is my fdisk. Sda has Vista and a backup partition, sdb has XP and Ubuntu, sdc my media disk and sdd is another back up disk. Thanks.

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf38df38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       55220   443546617+   f  W95 Ext'd (LBA)
/dev/sda2   *       55221      182401  1021581382+   7  HPFS/NTFS
/dev/sda5               2       55220   443546586    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dcf8dcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       54273   435947841    7  HPFS/NTFS
/dev/sdb2           54274       60801    52436160    5  Extended
/dev/sdb5           54274       60528    50243256   83  Linux
/dev/sdb6           60529       60801     2192841   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fba0c36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   42  SFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe81fe81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121601   976760001    7  HPFS/NTFS

```

---

### Post by Opt-Crysys on 2009-05-10
I am having sorta the same problem, I have xp on a different HHD, and I try to load it from GRUB and it wont, it gets to Starting up and turns of the comp completely, sorry if I'm budding in I just didn't want to make another post for this.

---

