---
title: "2 Hard Disks not showing"
date: 2005-11-09
forum: General Help
---

### Post by tig4 on 2005-11-09
Hey,

Post #2 here. 

Well, i am a switcher from OpenSuSe and I love ubuntu so far. However, my current setup is as follows:

MasterHD IDE1: Windows XP Build
SlaveHD IDE1: Ubunutu Breezy

MasterHD IDE2: Storage Disk

My problem is that I cannot access my Master HD on IDE1 or IDE2, they just don't show up. In Suse, they would be in a "windows" directory, but i cant seem to locate them in the filesystem.

I looked at dev/hda , and dev/hda1 but no luck.

Any ideas?

Thanks,

Tig

---

### Post by Kyral on 2005-11-09
They prolly aren't mounted yet.

Can I see the output from 

```
sudo fdisk -l
```

---

### Post by tig4 on 2005-11-09
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7169    57584961   83  Linux
/dev/hdb2            7170        7476     2465977+   5  Extended
/dev/hdb5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14946   120053713+   7  HPFS/NTFS

---

### Post by tig4 on 2005-11-09
Got it!

Thanks Kyral!

Tig

---

