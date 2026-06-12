---
title: "Accidentally changed filesystem type of mount partition during install.. help!"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by u_jim on 2009-06-06
I was reinstalling Ubuntu 8.04 a few days ago.  In the process, I wanted to also mount a couple of partitions (WinXP and Data).  The Windows and Data partitions did have files/data on them prior to this.  I believe I selected fat32 as the filesystem for the Data partition.  I did not select the format option during the mount configuration.  It's a 400GB partition, so it was probably ntfs.  Now I cannot access that partition.  I'm assuming that Ubuntu changed the fs type when I selected fat32.  Now Windows thinks that partition needs to be formated and gparted in Ubuntu thinks the fs type is unknown.

How do I fix this problem?  I do want my data partition to be back to normal and my files back!  Thanks for any help!

---

### Post by lindsay7 on 2009-06-06
If you do not have it get Gparted form Synatic and install it. Take a screen shot of your drive and post it here. The screen shot applet is in applications/accessories.

---

### Post by u_jim on 2009-06-06
Here's the output from fdisk and parted if it gives more clues.  I'm referring to sda5, the 400GB partition.

-------
sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d359d35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    21462839    10731388+   7  HPFS/NTFS
/dev/sda2        21462840    61496819    20016990   83  Linux
/dev/sda3        61496820   976768064   457635622+   f  W95 Ext'd (LBA)
/dev/sda5        63408618   903093974   419842678+   b  W95 FAT32
/dev/sda6       903094038   976768064    36837013+   7  HPFS/NTFS
/dev/sda7        61496946    63408554      955804+  82  Linux swap / Solaris

------------
(parted) print all                                                        

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  11.0GB  11.0GB  primary   ntfs         boot 
 2      11.0GB  31.5GB  20.5GB  primary   ext3              
 3      31.5GB  500GB   469GB   extended               lba  
 7      31.5GB  32.5GB  979MB   logical   linux-swap        
 5      32.5GB  462GB   430GB   logical                     
 6      462GB   500GB   37.7GB  logical   ntfs

---

### Post by u_jim on 2009-06-06
> **lindsay7 said:**
> If you do not have it get Gparted form Synatic and install it. Take a screen shot of your drive and post it here. The screen shot applet is in applications/accessories.

Here you go.  Screen shot attached.

---

### Post by u_jim on 2009-06-07
Here's the output for "blkid -c /dev/null".  I'm just following some diagnostics commands from another thread I found.  I just don't know how to apply anything to my situation.  Hopefully all this information is helpful.  I notice that sda5 isn't here.  That's the partition I'm concerned about.

--------
sudo blkid -c /dev/null
/dev/sda1: UUID="2460F0D260F0AC24" TYPE="ntfs" 
/dev/sda2: UUID="5fa954f7-728c-4333-8edd-e938a7a72553" TYPE="ext3" 
/dev/sda6: UUID="C87CFF967CFF7E0E" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: UUID="80b85d67-3bf4-4021-b56d-f6d7aa24613b" TYPE="swap"

---

### Post by lindsay7 on 2009-06-07
You should be able to right click on sda5 to unmount it then format it the way you want fat32 should be fine and windows and Ubuntu can boot read and write to it NTFS should be ok too and will accommodate larger files.  You may have to unmount sda3 first as this is the extended partition and holds sda5.

---

### Post by u_jim on 2009-06-07
> **lindsay7 said:**
> You should be able to right click on sda5 to unmount it then format it the way you want fat32 should be fine and windows and Ubuntu can boot read and write to it NTFS should be ok too and will accommodate larger files.  You may have to unmount sda3 first as this is the extended partition and holds sda5.

There were files on there that I want.  It seems like since I accidentally changed the filesystem type to fat32 on sda5 (which was ntfs before and had files on it), so it is now unreadable.  I want to change it back to ntfs and make it possible to get access to all my files.

---

### Post by lindsay7 on 2009-06-07
If you format it first the files will be lost. Gparted shows that that partition is unknown if it was fat32, it should be saying that, so I do not know.

---

### Post by u_jim on 2009-06-07
> **lindsay7 said:**
> If you format it first the files will be lost. Gparted shows that that partition is unknown if it was fat32, it should be saying that, so I do not know.

Yup.  Definitely not going to format that partition.  Not touching it until I get a positive solution.

---

### Post by lindsay7 on 2009-06-07
The other thing I am courious about is sba3 which is flaged lba. Are you able to boot Ubuntu now?

---

### Post by lindsay7 on 2009-06-07
The sba5 partition is showing that it is empty. How do you know there are files there now, if there were this would not be showing empty.

---

### Post by u_jim on 2009-06-07
> **lindsay7 said:**
> The other thing I am courious about is sba3 which is flaged lba. Are you able to boot Ubuntu now?

I am able to boot into Ubuntu and Windows fine.  Everything is fine except the Data partition.

---

### Post by u_jim on 2009-06-07
> **lindsay7 said:**
> The sba5 partition is showing that it is empty. How do you know there are files there now, if there were this would not be showing empty.

I assume that since I changed the filesystem type, the file list table (or whatever it's called) got wiped.  Where does it show that it's empty?

---

### Post by lindsay7 on 2009-06-07
When you look at the partition sda5 in Gparted the colored area in the partition is the used portion. There is none showing and the column marked "used" shows none, so my guess is that it is empty. I do not know how you would get to look into it if there are files there. So, if there are files there I am at a loss as to how to access them without a format of some type and that may delete what is there if anything.

---

### Post by lindsay7 on 2009-06-07
I found some info on this, I still not sure what is going on but this is a clue.

[http://gparted-forum.surf4.info/viewtopic.php?id=13381](http://gparted-forum.surf4.info/viewtopic.php?id=13381)

---

### Post by logos34 on 2009-06-07
you'll probably need to use testdisk to f[ix the partition table]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by nyk on 2009-06-07
> **lindsay7 said:**
> When you look at the partition sda5 in Gparted the colored area in the partition is the used portion. There is none showing and the column marked "used" shows none, so my guess is that it is empty. 

This isn't necessarily true, unless you've had this partition mounted and have attempted writing to it, chances are that the data is all still there, just *currently* inaccessible. I agree with those who posted before me. Testdisk is a powerful tool that has saved me before, and it can scan and read from the disk and informs you of any permanent changes before they happen. Just so you can be sure that it's a working solution. Best of luck!

---

### Post by u_jim on 2009-06-07
Thanks lindsay7, logos34, nyk.  I'm looking into testdisk now.  I installed the default version that's in Ubuntu 8.04.  Takes a while to scan for that partition.  Then when I tried to list the files, it segment faulted on.  I tried twice.

I manually installed testdisk 6.11.3 and it's currently scanning for the partition now.  It seems to take a bit longer even though it's a quick scan.  I hope this version doesn't segfault on me when I try to list files.  It's a big partition, 400GB.

---

### Post by u_jim on 2009-06-07
Thanks again guys.  I spent more this morning and the partition is back.  It look a long while for the deep scan to work under linux and also I rushed and exited the menus I needed to be in and had to restart the process.   I found the partition and it was apparently 'deleted', so I undeleted it.  Everything is back to normal.  I'll have to be more careful next time and backup my more important files.

Testdisk is a lifesaver.  Also you guys.  Thanks for letting me know about testdisk.

---

