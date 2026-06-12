---
title: "SD card fails to mount. No valid partition table."
date: 2009-06-25
forum: Hardware
---

### Post by Seine on 2009-06-25
Hi

I am trying to help my neighbour, who has just returned from a holiday to find her camera no longer reads her SD card. She had no backups and believes she has lost a lot of photos that mean a good deal to her.

When I insert the card into my Jaunty laptop:
[LIST]
[*]It is not mounted automatically
[*]I cannot manually mount it
[*]A new entry appears in `sudo fdisk -l` - see below
[*]gparted does not see the device
[/LIST]

Here is the fdisk -l output for the SD card.
```
Disk /dev/mmcblk0: 998 MB, 998768640 bytes
4 heads, 16 sectors/track, 30480 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0xeed8e734

Disk /dev/mmcblk0 doesn't contain a valid partition table
```

As it says there's a problem with the partition table, I live in hope that the data is still intact. But I do not know how to retrieve it. Can someone help me please?

---

### Post by adam_kimber on 2009-06-25
There are ways to clone the disk and restore partitions. Unfortunately most recovery programs are for Windows. There are all sorts around. 

Unfortunately (again) I have never recovered off a disk that has lost its partition table. 

I would recommend doing a byte by byte clone of the disk before attempting any recovery. I know this can be donw on HDD but not sure about SD cards. 

Sorry not be much more help.

---

### Post by Seine on 2009-06-27
Thanks anyway Adam. :D

---

