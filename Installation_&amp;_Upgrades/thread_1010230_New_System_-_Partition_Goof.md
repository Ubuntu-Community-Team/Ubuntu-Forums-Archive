---
title: "New System - Partition Goof?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Wataru_Daishi on 2008-12-13
Hey all, I have recently built myself a new comptuer and I decided that I wanted to give Ubuntu a shot.  So I read several threads and walkthoughs on how to install a Windowx XP / Ubuntu dual boot system.

I have a 650GB SATA HDD drive that I decided to split up thus:
70GB - Windows XP (NTFS)
502GB - Shared Data (NTFS)
70GB - Ubuntu (EXT3)
8GB - Swap

I also have a 160GB EIDE HDD that I was also going to use as a Shared Data drive (NTFS).

Per most recomendations, I installed Windows XP first (to include all 6,000 update and security patches =/ ).  After that I put in a CD install of Ubuntu.  I checked the CD, with no errors, and ran the install.

I tried to use the manual option for the disk partition to split the drives as shown above... however I got an error during this process which stopped the partitioning process.  Using the partition error again, my 650GB HDD is now only visible as a 590GB HDD .. and my 160GB HDD is listed as EXT3.  One of these two transitions has caused Windows XP to fail during bootup and I have not been successful in the Windows repair utility.

My current plans:
-Remove the 160GB IDE HDD - I think that it is adding a step of complexity (EIDE/SATA2) that I can avoid.  Can always install it after I get the dual boot rolling.
-Reinstall/Repair Windows XP
-Attempt to install Ubuntu again

My questions are:
-Did I miss something in my first attempt?
-Any suggestions?

---

### Post by tommcd on 2008-12-13
For now, to fix WindowsXP so it can boot, boot up your WindowsXP CD and run **fixmbr** from recovery mode. See this:
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

Some recommendations on partitioning:
8 GB is way to much for swap. Set up a 1 GB swap. If you have 1GB or more of RAM you will probably rarely use swap anyway.

Use manual partitioning from the Ubuntu install CD. Instead of 70 GB for Ubuntu, I would suggest a 12 GB root partition, and the rest for /home. That way if you reinstall the next version of Ubuntu all your data will be safe in /home.
Setting up a large data partition with NTFS to share with linux may be problematic. There is a program called NTFS-3G that can allow linux to read and write to Windows partitions. From what I have read NTFS-3G is much more reliable than it has been in the past. I have never used it though, so I have no experience with that. See this page:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

See this site for partitioning advice:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Per that page you could setup a large ext2 or ext3 partition and use FS-Drive to alow Windows to read your /data partition. BTW, that whole website is very good info for beginners.

Be sure to defragment windows before partitioning. And work on getting Ubuntu up and running on the 1st drive before trying to add the 2nd drive.

You could also try the Gparted live CD to partition the drive first. Then choose manual partitioning from the Ubuntu install CD and install Ubuntu to the 12GB partition you made for root, and then mount the other partitions duing the install. Try to partition with the Ubuntu install CD first though:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
And welcome to the Ubuntu forums!

---

