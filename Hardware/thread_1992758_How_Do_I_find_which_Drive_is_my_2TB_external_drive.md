---
title: "How Do I find which Drive is my 2TB external drive using &quot;fdisk -l&quot; ?"
date: 2012-05-31
forum: Hardware
---

### Post by spookyjack123 on 2012-05-31
Hello, I am using Ubuntu Server 12.04 for a small Minecraft server, and I am looking to have a backups plugin send backups to an external hardrive, over USB. however I am having trouble figuring out which drive is the external drive. my Drive is 2TB. Can someone tell me which one is the external USB drive ?

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bd70f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   295972863   147985408   83  Linux
/dev/sda2       295974910   312580095     8302593    5  Extended
/dev/sda5       295974912   312580095     8302592   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 8501 MB, 8501854208 bytes
255 heads, 63 sectors/track, 1033 cylinders, total 16605184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b7084e2

```

---

### Post by ahallubuntu on 2012-05-31
Only one drive is showing up: a 160GB drive on /dev/sda .  Are you sure your 2TB drive is plugged in and powered up?

---

### Post by spookyjack123 on 2012-05-31
> **ahallubuntu said:**
> Only one drive is showing up: a 160GB drive on /dev/sda .  Are you sure your 2TB drive is plugged in and powered up?
Yes, however it may be formatted in a format from Mac, can I view it to see if it is plugged in ? because it is plugged in, and it is powered up

---

### Post by spookyjack123 on 2012-05-31
It also seems to state
```

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

