---
title: "PACKARD BELL USB external hard-drive not showing"
date: 2010-06-20
forum: Hardware
---

### Post by Finny33 on 2010-06-20
Hello.

I recently reformatted the hard-drive on my DELL INSPIRON 1720 laptop and re-installed Ubuntu. Before doing all that, I saved all my files onto a PACKARD BELL USB external hard-drive.
Now, however, the external hard-drive doesn't show up and I can't access anything on it.

The result of fdisk -l in Terminal, gives me this :



Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       15338   123150724    7  HPFS/NTFS
/dev/sda3           15338       30401   120996545+   f  W95 Ext'd (LBA)
/dev/sda5           30010       30401     3148708+  dd  Unknown
/dev/sda6           15338       29408   113014784   83  Linux
/dev/sda7           29408       30009     4831232   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf04066ab

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27e9bfe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    b  W95 FAT32


dev/sda (my internal hard-drive) and dev/sdc (another external hard-drive by IOMEGA) seem to be fine, but the other external hard-drive (dev/sdb) doesn't show any information relating to partitions, etc.

Does anyone know what the problem might be ?

Thanks for looking and let me know if I need to provide any further information.

JOHN

---

