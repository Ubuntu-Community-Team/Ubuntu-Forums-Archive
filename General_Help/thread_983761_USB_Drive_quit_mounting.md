---
title: "USB Drive quit mounting"
date: 2008-11-16
forum: General Help
---

### Post by Phases on 2008-11-16
Recently my USB thumb drive quit mounting on one of my boxes (8.04 desktop), but works fine on the other (8.04 server) and at work (8.04 desktop). 

When I plug it in it shows up in Computer, and in Places, but double clicking it does nothing. Right click and say "mount" says either does nothing, or say "Unable to mount". 

sudo fdisk -l shows:

  ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 4110 MB, 4110230016 bytes
16 heads, 63 sectors/track, 7964 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x11e8bdd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7965     4013865    b  W95 FAT32

```

Any ideas?

---

### Post by Phases on 2008-11-16
Resolved. Replaced an card reader that was doing a number on my log files, little did I know, and everything works.

---

