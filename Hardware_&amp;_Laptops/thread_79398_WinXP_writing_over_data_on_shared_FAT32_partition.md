---
title: "WinXP writing over data on shared FAT32 partition"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by Sutekh on 2005-10-20
Hi, I have an extra hard disk in my setup that I meant to be shared by Ubuntu and WinXP.  It's formatted FAT32, and I can read, write and execute files on it from Ubuntu.  However once I restart and run Windows, all the data is gone.  I tried it the other way, writing in Windows and then booting Ubuntu, and the data remains intact.  Has anyone experienced this problem or could offer some guidance.

Thanks alot.

---

### Post by SickTwist on 2005-10-20
Never heard of this problem but I'll share some ideas. You might want to try partitioning and formatting the second hard disk from Windows. I don't know how your first hard drive is partitioned but if you don't put any primary partitions on the second drive Windows will not shuffle around your drive letters. Make the entire drive an extended partition containing as many logical partitions as you need. In linux the partition numbers will start with 5 (eg /dev/hdc5, /dev/hdc6, etc.) and in Windows the drive letters will just be appended to your existing ones with the exception of any optical drive letters--those will be changed unless you have them set manually to some high letter in the alphabet. Bleh, all this reminds me how much more elegantly Linux handles partitions. :)

Also, you may want to check out this [guide to partitioning]("http://fdisk.radified.com/"). You can ignore the fdisk directions if you want. The guide contains background information about partitioning and what the difference between primary, extended, and logical partitions are in case you're not familiar with those terms. Good luck!

Edit: Just to be certain, you should be mounting the partition in Linux as type vfat. Your /etc/fstab file should have a line that looks something like this if you want it to be automatically mounted at boot (be sure to change the device file to one that is appropriate):

/dev/sda6 /mnt/documents vfat defaults,umask=000,utf8 0 0

---

### Post by Sutekh on 2005-10-20
I'm pretty sure that the partition is being mounted as vfat (sounds very familiar), but I'll have to check when I get home.  I'll try partitioning it from windows and will see if that makes a difference.  Thanks for the link too, that'll give me some reading over lunch.

---

