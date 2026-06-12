---
title: "ubuntu cannot find extra (extended) hard disk drive"
date: 2018-01-16
forum: Hardware
---

### Post by courage2018 on 2018-01-16
I have installed a hard disk drive (~4TB) on my computer in addition to  the previous solid one (~200G), But I cannot find it anywhere. My system  is ubuntu-14.04 (64 bit).

When I type " sudo lsblk ", it shows:
```
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                            8:0    0 238.5G  0 disk
&#9500;&#9472;sda1                         8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                         8:2    0     1K  0 part
&#9492;&#9472;sda5                         8:5    0 238.2G  0 part
  &#9500;&#9472;ubuntu--vg-root (dm-0)   252:0    0 222.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1) 252:1    0  15.9G  0 lvm  [SWAP]
sr0                           11:0    1  1024M  0 rom
```    
And when I type " sudo fdisk -l ", it shows:
```

  Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00093873  
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   500117503   249807873    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   500117503   249807872   8e  Linux LVM  
  Disk /dev/mapper/ubuntu--vg-root: 238.7 GB, 238697840640 bytes
255 heads, 63 sectors/track, 29020 cylinders, total 466206720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000  
  Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table  
  Disk /dev/mapper/ubuntu--vg-swap_1: 17.1 GB, 17100177408 bytes
255 heads, 63 sectors/track, 2078 cylinders, total 33398784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000  
  Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```
  .

  I just wanna to use this new disk to enlarge my storage. Thanks for helping!

---

### Post by TheFu on 2018-01-16
Welcome to the forums.

Please use 'code tags' when posting command output. Too hard to read otherwise.
Please edit the OP and add.  Adv Reply (#).

If the disk isn't seen, there isn't much that can be done.
* Check the cable.
* Try a different port.
* Verify there is power to the disk.
* Look in 'dmesg' for the device.

---

### Post by courage2018 on 2018-01-16
Ok.

---

### Post by courage2018 on 2018-01-16
OK. I will see.

> **TheFu said:**
> Welcome to the forums.

Please use 'code tags' when posting command output. Too hard to read otherwise.
Please edit the OP and add.  Adv Reply (#).

If the disk isn't seen, there isn't much that can be done.
* Check the cable.
* Try a different port.
* Verify there is power to the disk.
* Look in 'dmesg' for the device.

---

