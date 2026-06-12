---
title: "Can Not See SD Card"
date: 2009-08-20
forum: Hardware
---

### Post by olebon on 2009-08-20
Hi,
I am running Ubuntu 9.04 on Acer Aspire One. Today I tried to read an SD card from my camera and it turned out that linux does not see it at all, while windows works fine. Can anybody help? Thanks!

root@oleg-laptop:/home# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12a3bs39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765       10130    75232395    7  HPFS/NTFS
/dev/sda3           10131       19457    74919127+   5  Extended
/dev/sda5           10131       19071    71818551   83  Linux
/dev/sda6           19072       19457     3100513+  82  Linux swap / Solaris
root@oleg-laptop:/home# dmesg

---

