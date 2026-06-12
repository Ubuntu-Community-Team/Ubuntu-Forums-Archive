---
title: "Problem - dual boot install win 7"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by eduardojuan on 2009-10-28
I've been unsuccessfully trying to do a dual install over Win 7.  I created a new 30GB NTFS partition using Win 7 already.  I have an Intel 64bit machine.  I am using the AMD64 installer.  When I get to the point of selecting the partition, the installer tells me: 

"NO ROOT SYSTEM FILE.  No Root System is defined.  Please  correct this from the partition menu".

I have no idea of how to do this.

Please advise regarding the correct dual boot installation.

Thanks.

---

### Post by presence1960 on 2009-10-28
when you get to the screen attached select manual. Then highlight the partition you are going to install ubuntu to and click edit. Select from the drop down box labeled "use as" the file system you want  (ext3 or ext4), then on mount point using the drop down select /.

This will define your root partition so the install can continue.

---

### Post by presence1960 on 2009-10-28
oops here is the pic.

---

### Post by eduardojuan on 2009-10-28
Thanks... I made it to the next step, I think. 

The pic you sent is not exactly like the image I get of the partitions, but close enough.  I am using 9.04.  I followed your directions, but now the message that comes up says I need to establish the SWAP partition.  Again, I have no clue!  I assigned a 30GB partition to Ubuntu so I should have enough space within that partition for swap files.  But how?

---

### Post by presence1960 on 2009-10-28
> **eduardojuan said:**
> Thanks... I made it to the next step, I think. 

The pic you sent is not exactly like the image I get of the partitions, but close enough.  I am using 9.04.  I followed your directions, but now the message that comes up says I need to establish the SWAP partition.  Again, I have no clue!  I assigned a 30GB partition to Ubuntu so I should have enough space within that partition for swap files.  But how?

Ok since you are doing a manual install I assumed you had all your ubuntu partitions set up already. You need to create a swap partition equal to the amount of installed RAM if you wish to use the hibernation feature.

I would use the partitioning program on the Live CD to create a swap partition. Boot the Live CD and choose "Try Ubuntu without any changes". When the desktop loads you can use gparted to do so. Go System > Administration > Partition Editor to run gparted.

If you need more detailed help post back.

---

### Post by eduardojuan on 2009-10-28
OK, I moved up to steps this time... but another issue arose.

I created a new NTFS partition (4GB), though I used Win 7 to do it since I am more familiar with it, and allocated it to swap.  Everything proceeded, but then:

"Error informing the kernel about modifications to partition /dev/sd5 *(NB_that should be the swap partition) *-- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda5 until you reboot-- so you shouldn't mount it or use it in any way before rebooting"

But if I reboot the install starts all over again and I will have to edit the partitions, which I believe, will put me into a vicious circle.

Once again, I would appreciate your advice.

---

### Post by Philk on 2009-10-28
Ubuntu will not use an NTFS partition for its swap partition.  In an automatic install, it would create the swap partition at the same time as it created the Linux partition.  Since you have started a manual install, you should go into gparted as the previous responder suggested and have gparted create a Linux swap partition.

Gparted will let you look things over in ways you will find reasonably familiar and then only change things when you are satisfied.

Good luck with it.

---

