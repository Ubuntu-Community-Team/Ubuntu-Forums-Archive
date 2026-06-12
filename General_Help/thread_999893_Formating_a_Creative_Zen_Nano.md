---
title: "Formating a Creative Zen Nano"
date: 2008-12-02
forum: General Help
---

### Post by mikeym on 2008-12-02
Hi all,

I've got a Creative Zen Nano flash MP3 player but I accidentally pulled it out while writing to it and messed up the disk. Now I decided I would format it with the following:

sudo mkdosfs -F 16 /dev/sdb1

which has left me with a disk that's unmountable. Any ideas? This is the output from *fdisk*:

```

fdisk /dev/sdb 
Note: sector size is 2048 (not 512)

Command (m for help): p

Disk /dev/sdb: 969 MB, 969932800 bytes
256 heads, 50 sectors/track, 37 cylinders
Units = cylinders of 12800 * 2048 = 26214400 bytes
Disk identifier: 0xa9a9a778

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          37      947100    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 50) logical=(0, 1, 1)

```

---

### Post by mikeym on 2008-12-02
It does appear on the system when I plug it in. It's just that I can't mount it.

---

### Post by mikeym on 2008-12-03
bump*

---

### Post by mikeym on 2008-12-04
Got it working the bit I needed was to set the sector size when formatting :

```

mkdosfs -F 16 -S 2048 /dev/sdb1

```

---

### Post by LightningCrash on 2010-02-01
> **mikeym said:**
> Got it working the bit I needed was to set the sector size when formatting :

```

mkdosfs -F 16 -S 2048 /dev/sdb1

```

Hey whaddaya know, fixed mine too.

Without the -F 16 it would gripe at me.

---

