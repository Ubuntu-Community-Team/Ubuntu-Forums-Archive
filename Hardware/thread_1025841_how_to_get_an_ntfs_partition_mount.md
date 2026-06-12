---
title: "how to get an ntfs partition mount"
date: 2008-12-30
forum: Hardware
---

### Post by dharkus on 2008-12-30
i've tryed fruitlessly b4 to mount this partition and to get it to mount automatically but can do neither
i've seen that this might be useful in my fruitless search for help:
sudo fdisk -l
```
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

### Post by xjcannonx on 2008-12-30
Do you have ntfs-config?

It is in the repo's and can read/write ntfs and can be net to automount a partition for you

I see your 400gb drive system type is sfs, are you using sfs to try to mount it...if so try using ntfs in the command instead

---

### Post by dharkus on 2009-01-02
ok - i'll check next time i'm on my ubuntu os as i'mm on my xp to use wow and itunes atm - shouldn't have to once i get that partition mounted - btw it's only part of the had drive that isn't mounted- the rest is but it's a sizeable amount

---

