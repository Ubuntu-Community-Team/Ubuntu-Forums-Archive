---
title: "Newbie making a huge mess"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Yojimbo1973 on 2009-09-10
:(
I recently installed the latest ubuntu on my HP TouchSmart tx2.
First I installed the 32 bit version for dual boot Vista or Ubuntu.
The 32 bit version didn`t work very well, so I decided to attempt to uninstall it.
FAILED....could not do it.

Next:
I installed the 64 Bit version of Ubuntu next to the other 2 OSs
Works better...at least I solved my no sound problem.

Now I have 2 installations of Ubuntu next to Vista on the same laptop.
But here is the more immediate problem........
I have an empty 12GB partition that was intended for ubuntu, but I was unsuccessful in installing to that partition.
As a result, whenever I try to install updates to ubuntu, it tells me that I have NO DISK SPACE? The Vista partition is 300GB.
I`m lost.:confused:

What I want to do it the following........

1. Un-install both installations of ubuntu from the Vista partition, remove it from the duel boot menu start up.
 
2. Re-install Ubuntu 64bit version onto the 12GB partition I created for it, and have Ubuntu actually use those 12GBs.

Anyone know how I could go about cleaning up the mess I made?

Thanks in advance.
:)

---

### Post by drs305 on 2009-09-10
You are a victim of a bug in the install program if you elected "side by side" install with Windows. The install by default makes the / partition only 2.5 GB, which is too small. You can reinstall or resize the partition.

Go to this thread, post 5. I've provided the information there which discusses your options:
[http://ubuntuforums.org/showthread.php?t=1260980]("http://ubuntuforums.org/showthread.php?t=1260980#5")

---

### Post by earthpigg on 2009-09-10
what i would do:

0. if you want to resize a windows partition, *do it from within windows before you start.* in my opinion, this is *always always always* how it should be done.

1. boot from a livecd. run gparted and delete both ubuntu partitions. leave the swap partition alone - or create one, if you dont have one already. 2gb is fine.

2. make another partition that uses up whatever space you dont want to keep on the windows partition. make it ext4 and have the boot flag.

3. click the install icon on the desktop. when the question comes up, 'manually partition'. (***always always always*** do this, in my opinion.)

4. set the 'mount point' of what will be your ubuntu partition as /. give it the flag of 'boot'. make sure it sees the swap partition as the swap partition.

5. if you get confused during the graphical installer, open up firefox from the live cd, navigate to ubuntuforums.org, and ask us for help before you randomly pick an uption you are unsure about.

---

### Post by Yojimbo1973 on 2009-09-11
Thank you very much for the advice.
I shall make the attempt this weekend and let you all know how it goes.

---

### Post by Yojimbo1973 on 2009-09-11
Ok...I got impatient and went ahead and reinstalled.......
I think I need glasses...the answer was right in front of my face during installation.
I deleted the older installs and installed Ubuntu to the proper partition this time.
I made the swap partition a little too big I think (5GB)...this leaves 9.4 GB on the install partition.
After full installation, Ubuntu reports I have 2.0GB of free space.
I think that should be enough, no?

But one unexpected thing happened.
When I load into Vista and have a look at My Computer......the Linux partition does not show up.
I see Local Disk C....but no Local Disk D.........
Why does Vista not see it?

---

### Post by drs305 on 2009-09-11
Congratulations on getting Ubuntu up and running. Yes, 5GB is too large for your swap. It won't hurt anything, but since you don't have a lot of space I would recommend you shrink it to 1GB, or 2Gb at most. You could then expand your / partition - it would not be hard if the swap and / are adjacent to each other. If you work with the Ubuntu partition, you will have to do it from the LiveCD or another rescue cd. For working with the swap partition, either running in Ubuntu or from the LiveCD, make sure you turn swap off (Partition, Swapoff in Gparted). 

I no longer use Windows so I don't know what capabilities have been introduced lately. There are applications that will allow you to work with ext2/3/4 file systems from within Windows. I'll provide a link but will mostly leave that part of the question for others. 

This is the download page, but do a search for Ext2IFS:
[http://www.fs-driver.org/download.html]("http://www.fs-driver.org/download.html")

---

### Post by raymondh on 2009-09-11
> **drs305 said:**
> 

this is the download page, but do a search for ext2ifs:
[http://www.fs-driver.org/download.html]("http://www.fs-driver.org/download.html")

+ 1

---

