---
title: "Change mountpoint"
date: 2008-08-23
forum: General Help
---

### Post by PsychedelicReaction on 2008-08-23
Hi guys. Today i wanted to check kubuntu with kde4.1 so i removed my previous opensuse11 installation. i used to keep my home directory in a different partition, but i forgot to set /home as its mountpoint during installation process.
This partition now is correctly mounted and i can browse it using dolphin, but of course in the wrong mountpoint. So i checked /etc/fstab but of this directory there's not any trace:

```
  GNU nano 2.0.7                  File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3
UUID=9b433895-6f9f-4cbc-919e-5d0f8f38145b /               ext3    relatime,errors=remount-ro 0 $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and this is my fdisk output (sda6 is the supposed home directory):

```
Disco /dev/sda: 160.0 GB, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+   6  FAT16
/dev/sda2               7        2617    20972857+   7  HPFS/NTFS
/dev/sda3            2618        3613     8000370   83  Linux
/dev/sda4            3614       19458   127274962+   f  W95 Esteso (LBA)
/dev/sda5            3614        3737      995967   82  Linux swap / Solaris
/dev/sda6            3738       19195   124166353+  83  Linux
/dev/sda7           19196       19457     2104483+   c  W95 FAT32 (LBA)

Disco /dev/sdb: 1019 MB, 1019215872 byte
14 heads, 45 sectors/track, 3159 cylinders
Units = cilindri of 630 * 512 = 322560 bytes
Disk identifier: 0x00000000

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3160      995203+   6  FAT16

```

Any idea of how to change mountpoint?

---

### Post by HalPomeranz on 2008-08-23
Add this line to your /etc/fstab:

```

/dev/sda6   /home     ext3    defaults        0       2

```

---

