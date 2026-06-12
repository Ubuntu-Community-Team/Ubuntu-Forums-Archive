---
title: "Computer won't boot with external hard dive"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Shaneggg on 2009-05-04
Installed Ubuntu yesterday and I restarted my laptop this morning without the external usb and i get a grub 21 error.

I think i need to transfer the MBR over to the internal one, but just don't know how. Would like vista (internal OS) to be the default and then have the option to pick Ubuntu when the external hardrive is plugged in. 

Here's some info on the partitions:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2              17        1322    10485760    7  HPFS/NTFS
/dev/sda3   *        1322       38587   299333628    7  HPFS/NTFS
/dev/sda4           38587       38914     2621440    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      108088   868216828+   7  HPFS/NTFS
/dev/sdb2          120386      121601     9767520   83  Linux
/dev/sdb3          108089      120385    98775652+   5  Extended
/dev/sdb5          108089      119879    94711176   83  Linux
/dev/sdb6          119880      120385     4064413+  82  Linux swap / Solaris


Thanking you in advance,
Shane

---

