---
title: "External hard drive problems"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by clericclark on 2007-04-24
I recently installed Dapper Drake and up until now i loved it. My external hard drive is no longer being read. I can't access it at all. It was working perfectly before. Any ideas? If you need more information let me know.

---

### Post by taurus on 2007-04-24
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by clericclark on 2007-04-24
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3378    27133753+   7  HPFS/NTFS
/dev/hda2            3379        7296    31471335   83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9679    77746536    7  HPFS/NTFS
/dev/sdb2            9680       36480   215279032+   f  W95 Ext'd (LBA)
/dev/sdb5            9680       22077    99586903+   7  HPFS/NTFS
/dev/sdb6           22078       36480   115692066    7  HPFS/NTFS

---

