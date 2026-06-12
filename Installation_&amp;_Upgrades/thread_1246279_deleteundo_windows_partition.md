---
title: "delete/undo windows partition"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by tamobe on 2009-08-21
Hello,

When I initially installed Ubuntu I partitioned my harddrive so I could dual boot and also run Windows XP.  I would like to work exclusively with Ubuntu and let it use the full harddisk and get rid of windows.  Any suggestions on how to go about doing this?

I'm currently running Ubuntu 9.04

Thank you.

---

### Post by presence1960 on 2009-08-21
boot into ubuntu and run in terminal ```
sudo fdisk -l
``` 
that is a lowercase L at the end. post the output from that command back here. You should have at least a couple ways to go with this, but we need to see your partition scheme.

---

### Post by tamobe on 2009-08-24
Hi Presence1960,

This is what i got:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc475c475

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        7322    17848183+   7  HPFS/NTFS
/dev/sda7            7323        9623    18482751   83  Linux
/dev/sda8            9624        9729      851413+  82  Linux swap / Solaris

---

### Post by presence1960 on 2009-08-24
You can boot off the Ubuntu Live CD and choose "try ubuntu without any changes", when the desktop loads you can use gparted to delete the sda1 partition which has the windows OS on it. You can access gparted either by opening a terminal and running ```
gksu gparted
``` or going System > Administration > Partition Editor.

You can then create a partition for storage with that space or merge it first with your extended partition and then adding it to a partition in the extended. I would go with the first option of making a data partition (ext 3) I would make it a primary partition.

---

### Post by tamobe on 2009-11-09
I would like to try this again - I have installed Karmic Koala.

Should I put it on a CD and boot from the CD?

---

### Post by ashsalama on 2009-11-09
here is the result retrived from "fdisk -l"

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd77024ab                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4867    39094146    7  HPFS/NTFS
/dev/sda2            4868       38913   273474495    5  Extended 
/dev/sda5            4868        5163     2377588+  82  Linux swap / Solaris
/dev/sda6            5164        9732    36699136   83  Linux               
/dev/sda7            9733       17029    58613121    7  HPFS/NTFS           
/dev/sda8           17030       21894    39078081    7  HPFS/NTFS           
/dev/sda9           21895       30407    68380641    7  HPFS/NTFS           
/dev/sda10          30408       38913    68324413+   7  HPFS/NTFS          

I need to move kubuntu files on sda1, any ideas?

---

