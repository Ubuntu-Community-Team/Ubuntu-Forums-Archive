---
title: "Can't Mount XP Anymore"
date: 2008-09-14
forum: General Help
---

### Post by umbrae on 2008-09-14
Hi!

I'm running Hardy and until yesterday, I was able to mount my Windows partitions, but now it's not allowing me to do so.

They show up, but when I try to open them, I get "unable to mount the volume."

NTSF-config tool is installed, however, when I try to check the boxes for the volumes, the Apply button grays out.

In terminal, I ran:
```
sudo fdisk -l
```

And this is what I got:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ca89ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3217    25840521    7  HPFS/NTFS
/dev/sda2            3218       38912   286720087+   f  W95 Ext'd (LBA)
/dev/sda5            3218       21064   143355996    7  HPFS/NTFS
/dev/sda6           21065       38912   143364028+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x944d944d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4351    34949376    7  HPFS/NTFS
/dev/sdb2            4352       38913   277619265    f  W95 Ext'd (LBA)
/dev/sdb5            4352       20358   128576196    7  HPFS/NTFS
/dev/sdb6           38878       38913      289138+  82  Linux swap / Solaris
/dev/sdb7           20359       38877   148753836   83  Linux

```

Help please!

---

### Post by Oldsoldier2003 on 2008-09-14
sometimes this is caused by the "dirty" flag being set on the NTFS filesystem. If you did an unclean shutdown of windows, just boot into windows and run the disk checker, then shutdown cleanly. Ubuntu should be able to mount your windows partitions fine. alternatively you can use the"-o force" option and mount the partitions.

---

### Post by bigbear2350 on 2008-09-14
you dont have to run chkdsk on unclean ntfs mount. Simply boot into windows and reboot. All windows does on an unclean ntfs mount is replay its journal, it would run chkdsk at boot if the journal replay failed for some reason.

---

### Post by umbrae on 2008-09-14
Thank you for your fast replies!

Yes, it was because I did an unclean shutdown. Logged to Windows and did a clean restart and now everything is working fine.

Thank you again. :]

---

