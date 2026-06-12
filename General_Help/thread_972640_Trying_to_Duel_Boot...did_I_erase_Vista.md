---
title: "Trying to Duel Boot...did I erase Vista?"
date: 2008-11-06
forum: General Help
---

### Post by Ivory-Shadows on 2008-11-06
Hey all. I'm completely new to Linux, but today I decided to start using it. I installed it on my laptop, and when it came time to partition my harddrive, I put asside 100 GB of Ext3 for /windows, 50 GB for swap, 100 GB of Ext3 for /home, and then the rest of my hard drive went to /  as Ext3 again.

Now when I'm trying to duelboot, I don't see the option to load Windows...just the three forms of Ubuntu. So am I trying to duel boot wrong? or did I manage to erase what was previously on my harddrive? 

help?

---

### Post by Sef on 2008-11-06
> Now when I'm trying to duelboot, I don't see the option to load Windows...just the three forms of Ubuntu. So am I trying to duel boot wrong? or did I manage to erase what was previously on my harddrive? 


Applications > Accessories > Terminal

Then paste or type this command:

```
sudo fdisk -l
``` small L, then paste the results here.   If you don't see an NTFS partition, then I would say you overwrote Vista.

---

### Post by lovinglinux on 2008-11-06
Windows can only read NTFS. Anyway, if you have formated the Windows drive with ext3, you certainly wiped it out. You could have mounted the Windows partition as /windows as long you didn't choose to format the partition. 

By the way, 50 GB for swap is way too much. Usually you only need 1.5 of the amount of RAM you have. So if you have 1 Gb RAM, your swap partition should have 1.5 Gb. How many drives you have and how many partitions you had before installing Ubuntu?

---

### Post by Ivory-Shadows on 2008-11-06
Here's the result from that code: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           24317       30401    48877762+   5  Extended
/dev/sda3           12159       24316    97659135   83  Linux
/dev/sda5           27970       30401    19535040   82  Linux swap / Solaris
/dev/sda6           24317       27968    29334627   83  Linux

Partition table entries are not in disk order




Looks like I did erase Vista...damn..that was dumb of me, haha. Don't suppose there's any way for me to get any of the data back, is there?

Before installing Ubuntu...I'm not sure how many drives and partitions I had...but not as many as now, I don't think...

I guess this leads to another question: what's the best way to go about altering my hard drive so I can reinstall Vista?

---

### Post by TeXtonyx on 2008-11-06
Some laptops come with a hidden partition used for reinstalling
Windows and drivers. Sometimes you get a recovery cd. Or if you
have a Vista install cd use that for the whole drive (unless you
have a hidden partition to keeep safe). 

Use Vista to resize the disk after Vista is installed. Shrink it
by however large you want your Ubuntu partition to become. 
During the Ubuntu live cd install, choose largest free space (guided).
This will keep Vista out of harms way.

At Step 7, Advanced, choose to install grub to the boot partition
not the MBR. You won't be able to boot Ubuntu yet, so in Vista
download and install Easybcd. Run it, and under Linux, add an
entry for Ubuntu (often its sda5). If you are not sure you can use
the live cd to boot up and then run: sudo fdisk -l which will tell
the name and number of the Ubuntu partition. You want type 83 ext3

---

