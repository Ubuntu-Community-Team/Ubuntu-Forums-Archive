---
title: "Ubuntu installation advice wanted"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by M11 on 2009-11-05
Hi
 
I'd like to install Ubuntu into my laptop, an Acer Aspire 5310, alongside Vista as a dual boot. The hard drive is 80gb partitioned already by Acer into two of 40gb. I currently have everything I use (system, boot etc) on my C drive with only about 7gb free and my D drive can easily be emptied. I was wondering if anyone could tell me whether it would be possible to use the D drive (primary partition according to the disk manager) to install ubuntu, or do I have to set up a new partition n my C drive to and install it here? Also, if both are possible, would you recomend I use the separate partitions already there, or re-partition the C drive for Ubuntu and Vista and use the D drive for saving documents and backups?
 
Thanks
 
M11

---

### Post by dhavalbbhatt on 2009-11-05
Technically, you should be able to re-format one of your partitions (I am suggesting "D" for the above mentioned reasons) and use that to install Ubuntu. At the time of installation, you will be asked what partition you want to use to install Ubuntu. At that point, select the "D" partition (Note: Ubuntu partition manager does not understand "C" and "D" - it will be somthing like sda0 and sda1). You will have to format the partition to one of the filesystems that Ubuntu understands (ext4 for Karmic).

---

