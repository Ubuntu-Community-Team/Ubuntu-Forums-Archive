---
title: "USB Drive not detected reguarly"
date: 2008-12-01
forum: Hardware
---

### Post by seren6ipity on 2008-12-01
I've a thinkpad T40 with xubuntu 8.04. I've had the same issue with ubuntu 7.10 on this laptop before.

The usb drive is detected some times for a brief period and then it disappears. Other times it never even gets detected.

lsusb entry is blank. 
I've usbmount, usbview and usbutils installed.

fstab entry is 
[SIZE="2"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=efc3632e-5f66-41c2-8416-1de63cbdac42 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=6f1e169d-b5e3-4423-b11a-fc4abcdb9e38 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[/SIZE]

---

### Post by lisati on 2008-12-02
I had trouble with a USB mouse and a USB keyboard working for a while then being ignored on my laptop, requiring a restart. Maybe [http://ubuntuforums.org/showpost.php?p=5353658&postcount=1](http://ubuntuforums.org/showpost.php?p=5353658&postcount=1) is what you're looking for.

---

### Post by seren6ipity on 2008-12-02
Thanks lisati. I followed the instructions on the thread you provided but still the behavior is same. It appears briefly and then again disappears.

Thanks for your time.

Additional information - When the usb was plugged in, I did sudo fdisk -l Following is the output - 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20480008+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            2551        4864    18587205    5  Extended
/dev/sda5            2551        4762    17767858+  83  Linux
/dev/sda6            4763        4864      819283+  82  Linux swap / Solaris

Disk /dev/sdb: 504 MB, 504102912 bytes
16 heads, 61 sectors/track, 1008 cylinders
Units = cylinders of 976 * 512 = 499712 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      797271     1966850   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(797270, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1966849, 14, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      172838     2156474   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(172837, 10, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2156473, 1, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     1915863     3899498   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1915862, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3899497, 9, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     3726667  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3726666, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by seren6ipity on 2008-12-06
Any ideas, anyone?

Thanks.

---

