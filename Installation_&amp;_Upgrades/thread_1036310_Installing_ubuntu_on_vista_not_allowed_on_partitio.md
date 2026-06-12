---
title: "Installing ubuntu on vista: not allowed on partition"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ~farah_r~ on 2009-01-10
Hi,

I am trying to install ubuntu by dual booting it with vista. I created a partition in my hard drive in vista and then loaded Ubuntu live CD. 

On the 'Prepare Disk Space' screen, I chose Manual since I don't want to lose Vista. I got the freed up space in the list, but I am not allowed to chose it. When I select it and click on Forward, I get the error:
No Root File System is defined. Please correct this from the partitioning menu.

I clicked on Edit Partition to check the options available. I have options to 'Use As', 'Format' and 'Mount Point'. Do I need to do something to these so that the computer allows me to install ubuntu on this hard drive?

Thanks...

---

### Post by chex_m8 on 2009-01-10
your mount point should be / 
create as primary partition
file system Ext3
good luck!!

I will point out you should also have a linux-swap partition. It's not totally necessary but it's the proper way of installing linux. Also it's nice to have a separate partition for data that is formatted with FAt32 that way when your in vista you can access the files and data you created in linux because windows doesn't recognise ext3.
heres a sample set up with a 100GB HD

40GB Windows
20GB Linux
2GB  Swap
38GB  FAT32

as a side note this arrangement cannot be done in Vista, you would be able to do this during the install by manually setting up the partitions.

---

### Post by Mark Phelps on 2009-01-10
If you used Vista to format the second partition, it most probably formatted it as NTFS -- which Ubuntu can't use for an installation.  As indicated, the Ubuntu partition needs to be formatted as Ext3.  If the installer won't do that, go back into Vista and remove the second partition, and then use the partition manager by booting from the live CD to format the partition for Ubuntu.

---

### Post by ~farah_r~ on 2009-01-10
> **chex_m8 said:**
> your mount point should be / 
create as primary partition
file system Ext3
good luck!!

I will point out you should also have a linux-swap partition. It's not totally necessary but it's the proper way of installing linux. Also it's nice to have a separate partition for data that is formatted with FAt32 that way when your in vista you can access the files and data you created in linux because windows doesn't recognise ext3.
heres a sample set up with a 100GB HD

40GB Windows
20GB Linux
2GB  Swap
38GB  FAT32

as a side note this arrangement cannot be done in Vista, you would be able to do this during the install by manually setting up the partitions.


I have vista and ubuntu working right now. I just have a question with all the partitions. I made a good mess out of them, I think. This is what I get through GParted:

1) /dev/sda2 ntcs 75.42 GB - This has my vista OS
2) /dev/sda1 ext3 74.70 GB -- This says 3.26 GB used, so am guessing this has Ubuntu
3) /dev/sda4 linux-swap 3.22 GB -- for the above linux os
4) unallocated 25.38 GB
5) /dev/sda3 extended 7.59 GB
6)      /dev/sda5 linux-swap 7.59 GB

Now, I was trying to use GParted to use that unallocated space. I couldn't install gparted using the ubuntu terminal. So, am using GParted through the Ubuntu Live CD. But, when I try to do it, it gives me an error saying that it is not possible to create more than 4 primary partitions. So, I will have to remove a primary partition. I don't want to delete something and mess things up. Any advice on how to use this unallocated space?

Plus, I also wanted to try and shrink the ubuntu partition. If I resize it using GParted, will I mess Ubuntu OS up or something?

---

### Post by chex_m8 on 2009-01-10
Yes it is true you can only have four primary partitions, the good news is that for some reason you have two swap partitions so you can delete the extended partition which contains the second swap partition.
Yes, you can resize the ubuntu partition and theoretically nothing should happen to your ubuntu install.

---

### Post by ~farah_r~ on 2009-01-11
> **chex_m8 said:**
> Yes it is true you can only have four primary partitions, the good news is that for some reason you have two swap partitions so you can delete the extended partition which contains the second swap partition.
Yes, you can resize the ubuntu partition and theoretically nothing should happen to your ubuntu install.

Thanks a lot...everything is sorted out now with respect to partitions...

---

