---
title: "SSD and Ubuntu 10.04 LTS"
date: 2010-07-10
forum: Hardware
---

### Post by dsub42 on 2010-07-10
Hi, I have just installed Ubuntu 10.04, I have connected a Crucial MLC SSD drive to my pc... but am wondering if someone could help me with the following?
 
Im new to linux so these may be stupid questions, but...
 
1. What do I format the drive as ex2, ex3? etc?
2. Is there trim support for SSD in this version of ubuntu?
 
Any help would be appriciated
 
Cheers

---

### Post by AltomineUK on 2010-07-10
There are no such thing as a stupid questions.......


1. Ext2, Ext3, Ext4 are all different types of Linux filesystems. An advantage of the Ext3 and Ext4 filesystems is that they support something called Journaling, which should help ur filesystem recover from any sudden interruptions (such as power failure etc.) as well as using less CPU resources. Ext2 does not support this feature. So I would recommend something like ext3 or ext4 over that matter.

If your SSD is an external (i.e. not the main one containing your Linux Filesystem) and you are intending to use it as storage, then there are other options.

2. Put simply.....No. While the TRIM is supported in the Linux kernel version 2.6.33 the current kernel that's running on Ubuntu 10.04 LTS at the moment does NOT make TRIM available to Storage drives (the latest ubuntu update has kernal 2.6.32).

Check around to see if you can find any programs that can send TRIM commands manually or something :S

---

### Post by sgosnell on 2010-07-10
But you can install later kernels.  I ran 2.6.33 for some time, and have been running 2.6.34 since it was released.  It's just a matter of downloading the .deb file and installing it, then rebooting.

---

### Post by AltomineUK on 2010-07-10
ok.....but, as I stated above, the current updated Kernel for Ubuntu is still 2.6.32 and it doesn't properly implement TRIM.

---

### Post by dsub42 on 2010-07-11
O.K thanks for your help...
 
Would any particular linux file system format be especially suited for database systems?

---

### Post by paulisdead on 2010-07-11
I'm using ext4 on my 40GB Intel SSD, and it's served me well.  Some argue to use ext2, since it doesn't do journaling and will minimize the writes.  I do like the recovery from unclean shutdowns that a journal provides, plus the faster fsck and boot times ext4 gives you.  You can run ext4 without a journal, but fsck will be run on any unclean shutdown.

In addition to installing the 2.6.34 kernel, I had to install an updated hdparm deb, so that I could have utilities to run the trim command.  Even then, I still had to get a more up to date version of the wiper.sh script, since the newer 40GB Intel drives weren't detected properly by the one bundled with the hdparm I installed.  You still have to manually run the wiper script to trim the drive, but it's pretty quick.  You can easily make it a cron job if you want it to run regularly.

I also followed these directions when partitioning and formatting the drive, to align the partitions on it [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

You can create the partitions manually from the livecd, and then not repartition during install, and install to the ones you made manually with fdisk in the directions.  I actually had a working Ubuntu install, and formatted the SSD from there, and just copied over my existing install, and slapped grub2 on it.

*Edit* I missed that you said for a database system.  Ext4 still has some issues with DBs.  I think there was a nobarrier option that could be toggled via fstab, that greatly improved performance, at the risk of data loss on an unclean shutdown.  I never had data loss with ext4 on the older kernels that didn't have it enabled, though.  I've also heard the 2.6.35 kernels are supposed to have better performance with ext4, as well, but haven't played with it myself yet.

---

### Post by shimoda on 2010-07-22
I used this method to confirm data trimming:
[http://www.ocztechnologyforum.com/forum/showthread.php?63843-The-truth-about-firmware-1.4-and-Linux&p=479503&viewfull=1#post479503](http://www.ocztechnologyforum.com/forum/showthread.php?63843-The-truth-about-firmware-1.4-and-Linux&p=479503&viewfull=1#post479503)

In my case, after trimming, only half of sector appears zeroed... I think that maybe partition is not aligned? :(

But fdisk -lu says:
> Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *        2048   125044735    62521344   83  Linux


---

