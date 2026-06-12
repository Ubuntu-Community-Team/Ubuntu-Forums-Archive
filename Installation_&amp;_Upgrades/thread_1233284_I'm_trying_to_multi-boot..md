---
title: "I'm trying to multi-boot."
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by knh94 on 2009-08-06
I'm trying to multi-boot, how am I supposed to write menu.lst?

Disk /dev/sda: 58.7 GB, 58765059072 bytes
255 heads, 63 sectors/track, 7144 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd380d380

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3526    28322563+  83  Linux
/dev/sda2            3527        3618      738990    5  Extended
/dev/sda3            3619        7143    28314562+   7  HPFS/NTFS
/dev/sda5            3527        3618      738958+  82  Linux swap / Solaris

---

### Post by merlinus on 2009-08-06
Post results of
```

cat /boot/grub/menu.lst
```

---

