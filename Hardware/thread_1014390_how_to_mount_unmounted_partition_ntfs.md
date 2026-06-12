---
title: "how to mount unmounted partition ntfs"
date: 2008-12-17
forum: Hardware
---

### Post by dharkus on 2008-12-17
i can't find anywhere other than [this]("http://ubuntuforums.org/showthread.php?t=283131") and [this]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") to help me mount an unmounted partition that was created by windows install - i.e. ntfs - the first is over complicated and hard to find the relevant bits as i only just started using ubuntu and for the second one the only simple one requires diskmounter which seems to be unavailable via the link
i've seen that this might be useful in my fruitless search for help:
sudo fdisk -l```

Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x970d11cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4982    40017883+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+  42  SFS
/dev/sdb2           16709       48641   256501822+  42  SFS
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14992    77953628    b  W95 FAT32
```
pls help me with this - i want to be able to access the system partition on my 400GB HDD as this has my program files on it from windows and as i only allocated 10GB for ubuntu without this extra space i won't be able to play games such as wow for which the game is 7.8GB and the updates are similar size
p.s. the 79.8GB volume is my ipod which is the main reason for me keeping windows as i can use itunes which seems to be the best i have seen for using ipods with and the best for other stuff aswell
oh yeh and i need it to automount when i boot up which would be really helpful

---

### Post by Ng Oon-Ee on 2008-12-17
The first link really contains all you need to know, from browsing through it. What easier way could be expected?

Its really set and forget, all you need to do is test the mount command in the terminal till you get the right combination of permissions (mainly you'd just want read-write), then you save it to your fstab, and never worry about it again.

Oh, and you get to learn a bit while doing so. Win-win all round, I would think. If you're expecting someone to come up with a 'click here and click there' set of directions, then you probably wouldn't be able to achieve what you want (to have a drive you can install to). You could always try loading up Nautilus, going to Places on the left-hand side and clicking on one of the drives which are not yet mounted (if you're using 8.10, drives which are mounted have this 'eject' button next to them).

---

### Post by dharkus on 2008-12-17
right ok so how do i get it to mount automatically - the link is faulty

---

### Post by dharkus on 2008-12-18
bump - come on guys - how do i get it to maount automatically?

---

### Post by dharkus on 2008-12-30
bump - i still don't know how to get it to mount automatically

---

