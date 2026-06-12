---
title: "major problems with second hdd"
date: 2009-11-11
forum: Hardware
---

### Post by maica22010 on 2009-11-11
ok so I recently started running ubuntu after windows died on my computer and I have been trying to recover files from my primary harddrive to my secondary harddrive with the only problem being when I first started my first drive was not even being recognized. After a lot of work I finally got it to be recognized and I started to  slowly transfer files to the secondary drive and treat my secondary as my new primary. Later I tried to to clone my primary drive to my secondary drive. But long story short it started giving a loop of i/o errors and ended up being forced to shut down before it could finish so now whenever I start ubuntu will only recognize my primary harddrive for mounting and recently I only get this when when I run fdisk -l

Disk /dev/sdg: 8015 MB, 8015314944 bytes
43 heads, 43 sectors/track, 8466 cylinders
Units = cylinders of 1849 * 512 = 946688 bytes
Disk identifier: 0xd528056a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           5        8467     7823424    b  W95 FAT32

****EDIT after I enter root mode I get this*****

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       63057   476710888+   7  HPFS/NTFS
/dev/sda2           63058       64601    11672640    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       63057   476710888+   7  HPFS/NTFS
/dev/sdb2           63058       64601    11672640    7  HPFS/NTFS

Disk /dev/sdi: 8015 MB, 8015314944 bytes
43 heads, 43 sectors/track, 8466 cylinders
Units = cylinders of 1849 * 512 = 946688 bytes
Disk identifier: 0xd528056a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           5        8467     7823424    b  W95 FAT32

The 1500 gb is my secondary while the 500 was the primary.

---

### Post by maica22010 on 2009-11-11
bump...
Just realized another problem ubuntu has also become unstable. Now I get lots of freezes and firefox has been crashing on me a lot. This wouldn't worry me much if not for the fact that that I'm not even running an installed version. I'm just running it from a usb and before this point no changes that I made have been saved.

---

