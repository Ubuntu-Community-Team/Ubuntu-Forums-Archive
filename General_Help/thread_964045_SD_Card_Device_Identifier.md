---
title: "SD Card Device Identifier"
date: 2008-10-30
forum: General Help
---

### Post by xnerdx on 2008-10-30
Okay here is what I did :). I used sudo fdisk /dev/sdb to edit the partition tables on my SD card, yes I have a reason to be doing so :O. Anyways, I went into the advanced settings and changed the Device Identifier to the default which is just 0's. I need to know what the ID should be because it won't let me mount it.

---

### Post by Wayne_V on 2008-10-30
Can you send the output of "sudo fdisk -l /dev/sdb" ?

Have you created a filesystem on the new partition(s) yet?

---

### Post by xnerdx on 2008-10-31
michael@michael-laptop:~$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 509 MB, 509083648 bytes
16 heads, 61 sectors/track, 1018 cylinders
Units = cylinders of 976 * 512 = 499712 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1018      496753+   b  W95 FAT32

---

### Post by xnerdx on 2008-10-31
Nevermind I just sadly steped into windows and formated it and it is better.

---

