---
title: "[SOLVED] Format External HDD from HFS+ to NTFS"
date: 2008-12-01
forum: General Help
---

### Post by gjr5017 on 2008-12-01
How do I format my external hard drive from HFS+ to NTFS. I've tried to figure it out in Gparted but it doesn't really do anything. It says that it formats it but it does not.

---

### Post by taurus on 2008-12-01
Can you post a screenshot of gparted for that harddrive?  Don't you have a windows that you can format that harddrive with?

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by gjr5017 on 2008-12-01
I am dual booting windows and ubuntu, however, windows does not recognize an HFS+ drive so I can't format it with windows.
Here is the output to my sudo fdisk -l
> coach@greg-pc ~ $ sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e85afb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1568    12594928+   7  HPFS/NTFS
/dev/sda2            3267       19457   130054207+   f  W95 Ext'd (LBA)
/dev/sda3            1569        3266    13639185   83  Linux
/dev/sda5            3267       19457   130054176    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/mmcblk0: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x555be4b2

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         983      495313+   6  FAT16

Disk /dev/sdb: 100.0 GB, 100030242304 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fe4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201    7  HPFS/NTFS


And here is a screenshot of gparted.

[IMG]http://i123.photobucket.com/albums/o285/gjr5017/Screenshot--dev-sdb-GParted.png[/IMG]

---

### Post by taurus on 2008-12-01
From the output, /dev/sdb1 is already a ntfs filesystem.

Otherwise, you need to unmount /dev/sdb1 first before you can reformat it.  Close down gparted and run this command to unmount /dev/sdb1.

```
sudo umount /dev/sdb1
```
Now, see if you can format it to ntfs with gparted.

---

### Post by gjr5017 on 2008-12-01
Ah that worked. Thanks. I did have the whole drive unmounted when I tried it the first time but its all good now. How do I rename it though? Its named as 100.0 GB Media and I'd like to change it to External Drive. Whenever I try to it says can't rename, available to only backend or something along those lines.

---

