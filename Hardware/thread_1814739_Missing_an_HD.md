---
title: "Missing an HD?"
date: 2011-07-30
forum: Hardware
---

### Post by AJLChase on 2011-07-30
When I first installed Ubuntu I had a windows drive....it was accessible and it was an xp 64 OS. Then I tried to install windows 7 so I could get my copy of Office 2010 to work since I need it for my Office courses at school, I had a failed install for reasons I can't recall..now when I'm in Ubuntu that drive no longer shows up. How do I a) get it to show up b) format it successfully so I can install windows 7 on it? Thanks!

---

### Post by coffeecat on 2011-07-30
Do you mean hard drive or partition? Windows uses the term "drive" loosely to mean either.

Anyway, boot into Ubuntu and post the output of this terminal command:

```
sudo fdisk -lu
```

---

### Post by AJLChase on 2011-07-30
Ok, here's what it shows with the command you just had me place.

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb9d5a6de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19535039     9767488+  83  Linux
/dev/sda2        19535040  1953520064   966992512+   5  Extended
/dev/sda5        19535103    39070079     9767488+  83  Linux
/dev/sda6        39070143    78140159    19535008+  82  Linux swap / Solaris
/dev/sda7        78140223  1953520064   937689921   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039dbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953519615   976758784    6  FAT16

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1250258624   625129281    c  W95 FAT32 (LBA)

---

### Post by AJLChase on 2011-07-30
I think the first drive shown is the one with ubuntu on it, the second one looks to be the one that won't show up...the 3rd one is my portable HD. Hope this helps!

---

### Post by coffeecat on 2011-07-31
Yes, your sda drive (1000GB) has your Linux partitions. Your second 1000GB drive, sdb has one large FAT16 partition on it. This certainly won't contain Windows 7. It should be accessible in Ubuntu unless the filesystem is corrupted, in which case Ubuntu will not automount it as a failsafe. Have a look in the left pane of a Nautilus file browser window. It should show up there. If there is a partition label, the label will show. Otherwise it will just say something like "1000GB filesystem". Clicking on it will mount it. If it doesn't show, then it's likely to be damaged, in which case you would have to reformat it.

Was there any data on that drive you need to rescue? What do you want to do with it? If it won't automount, I can give you some terminal commands to try to mount it, but my guess is that something is not right with it. A 1TB FAT16 partition is most unusual.

Your third drive, sdc, is 640GB, formatted FAT32. Is that your portable HD?

---

