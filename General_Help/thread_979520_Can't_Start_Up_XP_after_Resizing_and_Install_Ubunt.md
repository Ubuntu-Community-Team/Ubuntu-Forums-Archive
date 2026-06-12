---
title: "Can't Start Up XP after Resizing and Install: Ubuntu"
date: 2008-11-12
forum: General Help
---

### Post by Tekovro on 2008-11-12
I decided to resize my 300gb partition into two 150gb partitions and installed Ubuntu on the second one. Xp is still intact on the 1st partition but when the boot menu comes up asking me which OS to load i choose XP and it says"Starting up..." after waiting for 20 minutes i got impatient.

don't know if this helps..

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29c629c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18242   146527841    7  HPFS/NTFS
/dev/sda2           18243       36483   146520832+   5  Extended
/dev/sda5           18243       35737   140528556   83  Linux
/dev/sda6           35738       36483     5992213+  82  Linux swap / Solaris

```

---

### Post by Crafty Kisses on 2008-11-12
Not sure I can help, but someone else might be able to if you post the output of this command:
```
cat /boot/grub/menu.lst
```

---

### Post by TeXtonyx on 2008-11-12
I think you need to run TestDisk's rebuild boot sector. Directions:
[http://ubuntuforums.org/showthread.php?t=975789](http://ubuntuforums.org/showthread.php?t=975789)   Post #2

---

