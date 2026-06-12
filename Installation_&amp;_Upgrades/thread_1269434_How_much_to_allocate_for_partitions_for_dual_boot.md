---
title: "How much to allocate for partitions for dual boot"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by rmeske on 2009-09-18
After searching and reading many posts I have not quite found the answer I am looking for.  I have a new Studio 1555 laptop with a 500GB drive and Vista on it and want to make it into a dual boot.  

It seems like I will need a few partitions:

[LIST]
[*]Dell recovery partition
[*]Vista partition
[*]Ubuntu partition
[*]/home partition
[/LIST]
I am considering creating a separate partition for all my data in Vista and leaving one just for the OS and apps.  Can this partition be the same as the /home partition or should I have two different ones, one for Vista and one for Ubuntu?

Should I consider any other partitions or ways to configure this system?

And finally, how much should I allocate to the Ubuntu partition for OS and apps?  I have an existing install of Ubuntu on another laptop and it is currently using almost 15 GB.  So, I am considering something like 50 just to be safe.

---

### Post by oldfred on 2009-09-18
I have always liked the suggestions for a separate /data partition where you save all your user data. I did something similar several years ago as I was dual booting windows & Ubuntu and trying to convert from windows.
I created a FAT32 back then but suggest NTFS would be better now. I keep my data and both thunderbird and firefox profiles in the shared directory so whether I am in windows or Ubuntu I have the same email and same bookmarks. Now I am mostly in Ubuntu and have a new drive with a /data for linux only formated as ext3.
Since user data often is the larger you should not need as large of a root partition unless you are installing many large applications. Same for home, if home is just configuration files and not data it does not have to be very large. Of course size should not be critical with a 500GB drive as a few extra GB will not be the end of the world.

---

### Post by kasl33 on 2009-09-18
For me, I have a 160GB HDD in my Inspiron 1440 and I got rid of my Dell Recovery Partition (I have the Vista disk which will give me a clean install without all the bloatware) and I made my partitions like this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26950acf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6376        7225     6827625   83  Linux
/dev/sda3            7226       19457    98253540    5  Extended
/dev/sda5            7226        7555     2650693+  82  Linux swap / Solaris
/dev/sda6            7556       19457    95602783+  83  Linux

That all basically means that NTFS is 52GB, my / partition is 8GB, Swap is 2.7GB, and /home is all the rest - like 96GB.

---

### Post by stlsaint on 2009-09-18
> **rmeske said:**
> After searching and reading many posts I have not quite found the answer I am looking for.  I have a new Studio 1555 laptop with a 500GB drive and Vista on it and want to make it into a dual boot.  

It seems like I will need a few partitions:

[LIST]
[*]Dell recovery partition
[*]Vista partition
[*]Ubuntu partition
[*]/home partition
[/LIST]
I am considering creating a separate partition for all my data in Vista and leaving one just for the OS and apps.  Can this partition be the same as the /home partition or should I have two different ones, one for Vista and one for Ubuntu?

Should I consider any other partitions or ways to configure this system?

And finally, how much should I allocate to the Ubuntu partition for OS and apps?  I have an existing install of Ubuntu on another laptop and it is currently using almost 15 GB.  So, I am considering something like 50 just to be safe.


Do not have vista and windows on the same partition sharing root filesystem...bad look! and what do you mean by dell recovery and vista recovery? you should only need one...vista recover! so split your drive for both os...you can see sig for better details!

---

