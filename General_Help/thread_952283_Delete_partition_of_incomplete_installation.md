---
title: "Delete partition of incomplete installation"
date: 2008-10-19
forum: General Help
---

### Post by mcalica on 2008-10-19
Hello everyone, I am new to this forum so excuse my noobness.  I recently tried installing Ubuntu to my computer.  This was a dual boot with Vista.  During the installation, though, my computer decided to shutdown before the installation was complete.  I went back and tried to reinstall, but it showed that the partition was filled; the only option I had was to do a full disk install (and wipe out my Vista as well).  I used the live cd to get into Gpart and saw that I could adjust the amount of partition space, but the vista and ubuntu partitions were connected and the only way to delete the ubuntu was to delete the Vista part as well; I couldn't separate the two.  So I guess to make a long story short, how do I get rid of that incomplete ubuntu partition?  I don't think grub was installed, because when I boot my computer, it goes straight to Vista...NO mention of Ubuntu during startup.  Someone PLEASE help!  Thanks in advance.

---

### Post by NorthernLights on 2008-10-19
Hi,

I did not fully understand your matter. For the going straight to Vista thing, I say you need to re-install grub. Boot from a live cd to restore grub ("sudo update-grub"; check man pages and google).

---

### Post by mcalica on 2008-10-19
actually, I repartitioned for a new Ubuntu install, but how do I get rid of that old Ubuntu partition that didn't fully install itself?

---

### Post by Monotoko on 2008-10-19
boot into your live CD, and post the output of
```

sudo fdisk -l

```

---

### Post by mcalica on 2008-10-19
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b3ef5b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6446       60801   436614570    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       48163+  de  Dell Utility
/dev/sdb2               7        1312    10485760    7  HPFS/NTFS
/dev/sdb3   *        1312       38914   302034944    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 750.1 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      266306  2147483647+  ee  GPT

Disk /dev/sdd: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         976     7839698    b  W95 FAT32

This is what I got with the above command...Also, when I tried repartitioning with Gpart, it showed an error and I still cannot use the freespace that it created on my harddrive.

---

### Post by mcalica on 2008-10-21
can anyone help me out?

---

### Post by mcalica on 2008-10-22
man, no love in these forums.

---

