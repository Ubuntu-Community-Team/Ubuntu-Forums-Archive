---
title: "Hard disk need to be extended increased from vmware"
date: 2013-08-18
forum: Hardware
---

### Post by chiranga on 2013-08-18
I'm using 12.04 ubuntu server edition on VMWare Hypervisor. Earlier I had 24GB hard disk allocated to this virtual server and I need to extend it to a 100GB for the same mounting point. Is it possible to do so? So I increased disk size from 24GB to 100GB. 

When I use fdisk-l following shows.

root@testwebserver:/home/user# fdisk -l


Disk /dev/sda: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008cf6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    52426751    25962497    5  Extended
/dev/sda5          501760    52426751    25962496   8e  Linux LVM

when I execute df -h following shows.

Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/testwebserver-root   23G  9.8G   12G  46% /
udev                           1000M  4.0K 1000M   1% /dev
tmpfs                           403M  240K  403M   1% /run
none                            5.0M     0  5.0M   0% /run/lock
none                           1007M     0 1007M   0% /run/shm
/dev/sda1                       228M   48M  168M  23% /boot


I need to extend /dev/mapper/testwebserver to 100GB.
But I'm not sure how to do it. Please help me. I'm a newbie to ubuntu.

---

### Post by chiranga on 2013-08-18
Followed the steps as described in below and get it worked out.


[http://www.joomlaworks.net/blog/item/168-resizing-the-disk-space-on-ubuntu-server-vms](http://www.joomlaworks.net/blog/item/168-resizing-the-disk-space-on-ubuntu-server-vms)

---

