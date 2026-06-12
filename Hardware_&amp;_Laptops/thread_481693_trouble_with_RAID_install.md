---
title: "trouble with RAID install"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by bikeman1 on 2007-06-22
I have a 3ware 9650 raid card (SATA, 8 port) that is installed and operating fine under 7.04.  I have 4 drives installed as a working array in half the ports as sda1 -- they also are working fine.  But I am having difficulty installing 4 drives as a second array in the other 4 ports.  They are used drives so I am wondering if I have some bad sectors or something, and how to deal with this.  They are all of the same brand and age (Maxtor YAR51HWO) within the array.  3ware assures me there should be no drive compatibity issues related to BIOS of drives.  

The 4 drives are recognized fine by the 3ware's array manager, and Ubuntu sees the array and assigns it to /dev/sdb.  Also seems to be the right size.   So far so good.

I create a new primary linux partition /dev/sdb1, using the entire drive space.  
This is where things break down.  If I try to format the drive 

fdisk runs like this:

[INDENT]calling ioctl() to re-read partition table

WARNING: re-reading partition table failed with error 16: device or resource busy

The kernel still used the old table
New table will be used at next reboot.
Syncing disks.

[/INDENT]Then X chimes in with an error "Cannot Mount Volume".  Upon rebooting, <<neither>> array can be detected by the card -- its locked out.  I can restore the installed array by pulling the plug on the failed array, but I can't even get to the format step on it.  

So the question -- why won't fdisk modify the partition table?  All I can think is that there are disk errors on the drives that need to be formatted.  The 3ware raid card does not perform low level formatting on the drives when building the array.

Anyone have any ideas or suggestions?  I have thought of trying to install each drive independently (non-raid) and formatting each drive with ECC correction one drive at a time -- but I honestly don't know enough about RAID cards to know what to do.  Maybe I need more support from the card vendor.  Or maybe I just need to trash the old drives....

---

