---
title: "Please help, Ubuntu does not detect partitions on my new HDD. trying since a month."
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by Ketansa on 2009-08-08
Hallo friends experts and users,  Please help me. I have been trying to install Ubuntu 8.04, 9.04, Ubuntu Studio 9.04, Kubuntu 9.04, and others like SUSE, on my new 1tb hard disk. I have created 4 primary NTFS partitions on it through windows disk management. None of the OS installers list them at the boot. These Live CDs detect all the partitions on my old hard disk, but the new 1tb hard disk is listed as one device (with no partitions). I have formated the partitions (on my new HDD) one by one very correctly with no errors. Why arent they showing? What should I do?  Please tell, thanks, good wishes, see you. Ketan.

---

### Post by Ketansa on 2009-08-08
Hi, sorry by reading my post I just thought that it is too elongated. so in short-
The Ubuntu installer shows an empty, non partioned, totally unallocated disk of my new 1tb Hard disk. But regarding my old 400gb Hard disk, it is showing all parittions.

They(new) show and work well in my other dual boot os. Also running xp on one of its partition without any problems.
Please give me solution.

---

### Post by presence1960 on 2009-08-08
Try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

FYI Linux does not install to NTFS or FAT partitions, linux uses ext 3 or ext 4 filesystems (and a few others, but not windows filesystems!). I would use the [gparted live CD]("http://gparted.sourceforge.net/livecd.php") to partition the disk.

---

### Post by themusicalduck on 2009-08-08
Do you want to install ubuntu to one partition and keep 3 other ntfs partitions on the drive?

It might be worth using gparted on a live CD to partition the drive how you want, and then install ubuntu afterwards. Using gparted, you can create an ext3 (or 4 if you like) for root and another as swap (as an extended partition, since you're limited to four primary partitions) and then select the partitions at install.

Or if it seems like an easier solution, reformat the entire drive at installation, install Ubuntu and then resize the partition and create the other NTFS partitions with gparted again on a live CD.

---

### Post by louieb on 2009-08-08
> **Ketansa said:**
> ..The Ubuntu installer shows an empty, non partioned, totally unallocated disk of my new 1tb Hard disk...

The Ubuntu installer and Gparted too will show an empty disk when they find it has a non-standard partition table. 

Windows has a bad habit of putting a primary partition inside of an extended partition.  Just a guess thats what happened to you.  

Do you have internet when using a live CD? If so open a terminal window and copy and paste the output of 
```
sudo fdisk -l
```
Lowercase L at the end. Standard or not fdisk will list the content of the drives partition table.

---

### Post by presence1960 on 2009-08-08
> **louieb said:**
>  

Windows has a bad habit of putting a primary partition inside of an extended partition.  Just a guess thats what happened to you.  



One of many bad habits :D

---

### Post by Ketansa on 2009-08-08
Hallo Hallo, :-) presence, themusicalduck and louieb,

Thank you for teling me all this. It was detecting all the ntfs partition on my old hard disk. But actually the problem was due to bad partitioning. I used O&O disk manager to partition two parts, and then I used another software and also windows disk management utility to create other partitions. This created some overlapping error of the partitions which lead then non-detectible.
I then deleted them all and re-partitioned them with PM8 only. Now the Ubuntu installer detects them.
After my post went behind in the list I went off, and couldnt have idea that someone will reply to me. But thank you for telling me all that :) because I came to know that I have to create ext3 or ext4 to install the Kubuntu.
But what is swap? Is it something like Page files (of windows)? Do I have to create an extended partition for swap?
thanks, talk to you again.
Ketan.

---

### Post by presence1960 on 2009-08-08
> **Ketansa said:**
> Hallo Hallo, :-) presence, themusicalduck and louieb,
Thank you for teling me all this. It was detecting all the ntfs partition on my old hard disk. But actually the problem was due to bad partitioning. I used O&O disk manager to partition two parts, and then I used another software and also windows disk management utility to create other partitions. This created some overlapping error of the partitions which lead then non-detectible.
I then deleted them all and re-partitioned them with PM8 only. Now the Ubuntu installer detects them.
After my post went behind in the list I went off, and couldnt have idea that someone will reply to me. But thank you for telling me all that :) because I came to know that I have to create ext3 or ext4 to install the Kubuntu.
But what is swap? Is it something like Page files (of windows)? Do I have to create an extended partition for swap?
thanks, talk to you again.
Ketan.

Swap is like windows paging file. Swap can be either a primary or inside an extended partition. That is dependent on what your partition needs are. Either way will work.

---

### Post by raymondh on 2009-08-08
> **presence1960 said:**
> Swap is like windows paging file. Swap can be either a primary or inside an extended partition. That is dependent on what your partition needs are. Either way will work.

With 4 partitions existing, you might want to make one of them EXTENDED and put swap inside it ... as well as others like root, etc.

As presence said, it's like a paging file.  Its' use is dependent on your requirements (hibernating) and regular app usage ..... consider swap a spill-over bin for RAM.  Most advocate 1-2X RAM but I find that rule valid only for low-RAM situations.  I use 1.5GB SWAP and rarely even get to use it ... even in a 2GB RAM system.

Good luck.  Back up your files.

---

### Post by Ketansa on 2009-08-08
oh ok, I then would create the swap partition on another hard disk. Should it be same ext3 format if the OS is ext3?

---

### Post by raymondh on 2009-08-08
> **Ketansa said:**
> oh ok, I then would create the swap partition on another hard disk. Should it be same ext3 format if the OS is ext3?

It'll format on its' own .... LINUX FILE SYSTEM... something like that. Can't remember the exact details as it has been a while. 

Just mount it as SWAP and let the installer do it for you.

---

