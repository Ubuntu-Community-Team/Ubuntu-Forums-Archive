---
title: "Need help deciding what to do with new 9.04 install"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Norman Thom on 2009-05-01
I am not a <brand new> user just an idiot I suppose.

I have a PC running windows XP
I wanted to dual boot with Ubuntu 9.04 ( I have done this with earlier versions in the past ).  So I stuck in the install disc for ubuntu and noticed there was an option for "install side by side and decide at start up" (not actually verbatim).  so I did this.
It then asked for a new parition for ubuntu and one for the swap file so I created those (I think) at 20GB and 2GB respectively.I then installed Ubuntu. To my amazement at boot up grub only gave me the option to boot into Ubuntu. I did. I checked the file system properties and found it had 167,000+ files for 58.9GB with 15.0GB free.  The files for Win XP must still be there but I cannot access them or boot into XP.  Can anyone suggest a solution to this problem, please help

---

### Post by taurus on 2009-05-01
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Norman Thom on 2009-05-01
Thanks for the quick response Taurus:

the response is as follows:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7025    56428281   82  Linux swap / Solaris
/dev/sda2            7296        9729    19551105    5  Extended
/dev/sda5            7296        9729    19551073+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77e177e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
ellysium@ellysium-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  2.5G   15G  15% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  168K 1007M   1% /dev
tmpfs                1007M   84K 1007M   1% /dev/shm
lrm                  1007M  2.4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             150G   59G   91G  40% /media/File Store
ellysium@ellysium-desktop:~$

---

### Post by taurus on 2009-05-01
Did you have windows on the first harddrive, /dev/sda, while /dev/sdb1 is either your second harddrive or a USB drive?

If you have windows on the first harddrive, it's gone.  You just installed Ubuntu over it.

---

### Post by Norman Thom on 2009-05-01
Thanks Taurus:

Not what I wanted to hear. . . but what the heck.
Do you know of any way I can install Windows to dual boot with Ubuntu already there I can always rebuild from my back up drive

---

### Post by Norman Thom on 2009-05-01
Taurus:

Note the extended partition.  Could I add XP there?

---

### Post by taurus on 2009-05-01
I don't think windows would be happy to be in the logical partition.  Therefore, you need to install it on a primary.  You can resize the harddrive, making room to create another primary partition for windows but that takes a little of work.  

The easiest way is to boot your machine with Ubuntu LiveCD.  Then use gparted (System -> Administration -> Partition Editor) and remove all the partitions.  You probably have to unmount the swap partition first (right click /dev/sda1 and swapoff) before you can delete it.  Then, create two partitions: /dev/sda1 & /dev/sda2.  Format /dev/sda1 to ntfs and /dev/sda2 to ext3.  Install windows to /dev/sda1 first and then tell Ubunbu installer to install it on /dev/sda2.

---

### Post by Norman Thom on 2009-05-01
Thank you for all your help Taurus:

I'll probably just wipe my disc, reinstall windows use gparted to create another partition and load ubuntu.  Thanks for your efforts

---

