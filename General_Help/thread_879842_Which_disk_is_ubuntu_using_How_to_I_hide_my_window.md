---
title: "Which disk is ubuntu using? How to I hide my windows partitions?"
date: 2008-08-04
forum: General Help
---

### Post by junkmonk on 2008-08-04
I have a triple boot system, XP, Vista, Ubuntu 8.04. I am brand new at Ubuntu 8.04, I've been searching all the web for an answer to my questions and have been generally successful, but this still trumps me.

In Windows XP drive C: is the Windows XP Install Partition
              drive D: is the Windows XP Programs/Games Directory
              drive E: is Daemon-tools Virtual CD/DVD drive
              drive F: is actual DVD drive
              drive G: is Windows Vista Install Partition
              drive H: is Ubuntu (Installed with Wubi from XP)

I Made drive H: 20 gigabytes, and selected the 15 gigabyte install in Wubi.

Now, in Ubuntu:

In the 'Places' menu at the top, underneath computer, there is:
CD/DVD Creator
Windows Vista ( drive G: )
Programs ( drive D: )
Windows XP ( drive C: )
Where's the Ubuntu drive?

When I click on computer itself, I see the same drives (except CD/DVD creator is CDRW/DVDRW drive) PLUS there is something called Filesystem which has a different icon then the other drives. It is full of folders like bin, boot, cdrom... I figured this is drive H: at first, but I tried to save a file to it (and extract into it) and both give me access denied errors. So, clearly this is some kind of system directory? This leaves me ONLY the Windows Vista, Programs, and XP partitions to save and install into; I don't want to install into these as these are being used by Windows, and I don't want them cluttered. 
Do I have to make a new partition?
Is the drive that you install Ubuntu into never visible?
When I save to my desktop, in which drive is that going? Why is that drive not visible? 
I want to have a dedicated DEFAULT ubuntu installation/download drive/partition (I thought it was drive H but can't find it).

Now, what really boggles me, is when I open the Disk Usage Analyzer.

It says: Total filesystem usage: USED 19.4 GB AVAILABLE: 26.0 GB (TOTAL FILESYSTEM CAPACITY 45.4GB)

Why is the total capacity 45.4 GB if the drive I installed Ubuntu into is only 19.4 GB???
And is it actually using 19.4 GB, or is that reserved space for swap etc.?

Also, most importantly: Once I have a dedicated drive/partition for ubuntu, I want to complete hide the Vista/Programs/XP hard drives from places/computer/wherever else they may be visible... (I can hide hard drives in XP/Vista easily but how do I do this in Ubuntu) 

PS sudo gedit etc/fstab does NOT look like it shows the XP, Vista, Programs Drives... it only shows some /host/ubuntu/disks and cdrom0 and floppy0. Here is the entire copied result of sudo gedit etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Help me linux masters!!
Thank you in advance to everyone that contributes!!!

---

### Post by castor_troy on 2008-08-04
Welcome to the Forums !

The drive called filesystem is the drive on which ubuntu is installed. Navigate to Filesystem -> Home -> (your username). You can use this freely.

Ubuntu makes mistakes when calculating disk capacity of ntfs drives. It even happens to me. 

If you dont want the drives to be visible just rt click on the drive and click unmount drive. All the drives apart from the one on which you have installed ubuntu will not be mounted by default. So you dont have to worry about it.

____________________________________________________________________________

If this post helped you dont forget to click on the yellow star at the bottom right of the post.


Cheers !

---

### Post by bodhi.zazen on 2008-08-04
Linux Partitioning is a little different.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by junkmonk on 2008-08-04
> **castor_troy said:**
> Welcome to the Forums !

The drive called filesystem is the drive on which ubuntu is installed. Navigate to Filesystem -> Home -> (your username). You can use this freely.

Ubuntu makes mistakes when calculating disk capacity of ntfs drives. It even happens to me. 

If you dont want the drives to be visible just rt click on the drive and click unmount drive. All the drives apart from the one on which you have installed ubuntu will not be mounted by default. So you dont have to worry about it.

____________________________________________________________________________

If this post helped you dont forget to click on the yellow star at the bottom right of the post.


Cheers !

Okay filesystem/home thank you that helps. However, the disks are already unmounted as when I right click on them in 'computer' the only option is mount.

Is there any way to fix the way it views NTFS partitions? Should I have installed it on a FAT32 partition?

---

### Post by LowSky on 2008-08-04
I'm not a fan of Wubi, while it does work, it has some extra glitches that a regular ubuntu install would not have. Linux wasn't designed to run on a NTFS or FAT32 files system, so it does make some errors when making calculatons of disc size.

---

### Post by castor_troy on 2008-08-05
@ Junkmonk

what do you exactly mean by "fix" the way it views your ntfs partitons ????

The wubi install is gud for trial purposes. The perfomance is not all that good. Disc usage is very high.

If you are satisfied with your Ubuntu experience then i would recommend to uninstall the present install through wubi and go for a fresh install.

Installing on ntfs or fat32 wont do any good. It's best installed on an ext3.

__________________________________________________ __________________________

If this post helped you dont forget to click on the yellow star at the bottom right of the post.


Cheers !

---

