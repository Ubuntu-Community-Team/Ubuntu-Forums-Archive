---
title: "can't mount external drive"
date: 2008-04-27
forum: Hardware
---

### Post by Baje on 2008-04-27
I have a toshiba satellite running ubuntu 7.1.  I have an external seagate freeagent drive.  I am unable to mount it.  lsusb provides the following output:

Bus 005 Device 002: ID 0bc2:3000 Seagate RSS LLC 

fdisk -l provides:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


I have tried: sudo mount -a but got the following error:
fuse: failed to access mountpoint /media/external: No such file or directory

I am somewhat of a novice. I have heard that I need to edit my fstab file but im not really sure what that means/how to do it.

Thanks for any help!

---

### Post by Baje on 2008-04-27
bummmp please help

---

### Post by masticate on 2008-04-27
Please print the results for the following:
[LIST=1]
[*]cat /etc/fstab
[*]ls -la /media
[*]ls -la /media/external
[/LIST]

---

### Post by justotech on 2008-04-28
You can also try force mounting it.

sudo mount /dev/sda1 -o force

Obviously you'll need to know what the OS calls your portable.  That's what I used to have to do with my portable to make KDE like it.  It turned out that I needed to do the "safely remove" option when I disconnect it from a Windows box.  Once I started doing that and unmounting it with Linux it works fine.

---

