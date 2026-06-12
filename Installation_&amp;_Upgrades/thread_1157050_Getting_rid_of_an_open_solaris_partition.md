---
title: "Getting rid of an open solaris partition"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by brentrubeck on 2009-05-12
Hello,  I think I have kind of figured out how to get rid of my solaris partition, but I would like to run it by someone before I attempt it.  From the results of fdisk it looks like the boot flag was set to the solaris partition and that the /boot partition that was originally put on my machine hasn't been touched too much (I've had to go in to it and delete older kernels and change the menu.lst on the solaris partition).  

So here's the big question can I configure grub from a linux partition and restore the backed up copy of my menu.lst and then reboot?  The results of find /boot/grub/stage1 on the linux partition were (hd0,6).  Also will I need to fdisk from a live CD and set a new boot flag for /boot or will grub handle that stuff?  Thanks

First here's a list of my partitions (fdisk results are below):
sda1 - Windows partition
sda2 - Original boot partition
sda3 - Solaris Partition
sda5 - Personal Linux partition
sda6 - Swap
sda7 - Linux partition used for development
sda8 - Shared space

Here's results of the fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b40849d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896    7  HPFS/NTFS         
/dev/sda2            1568        1580      104422+  83  Linux                
/dev/sda3   *        1581        3492    15358140   bf  Solaris
/dev/sda4            3493       30401   216146542+   5  Extended
/dev/sda5            3493        5520    16289878+  83  Linux
/dev/sda6            7433        7687     2048256   82  Linux swap / Solaris
/dev/sda7            5521        7432    15358108+  83  Linux
/dev/sda8            7688       30401   182450173+  83  Linux

---

