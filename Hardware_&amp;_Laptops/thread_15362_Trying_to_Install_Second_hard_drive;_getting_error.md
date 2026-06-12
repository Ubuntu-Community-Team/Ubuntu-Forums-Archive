---
title: "Trying to Install Second hard drive; getting error message"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by ryharv on 2005-02-13
Hello everyone:

This is my first post, so please bear with me:

I installed Ubuntu on my machine, and now I'm attempting to install a second (slave) hard disk.  The disk is recognized in Device Manager as IDE (Slave).  When I run **fdisk -l** from the command line, it sees:

>    
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401    5  Extended 

This is the new drive, so I know the system is recognizing it.  

I have already set up the new drive using **fdisk /dev/hdb**, and now hdb1 shows up in the **/dev/** directory.  

As I understand it, my next step is to run **mkfs -t ext3 /dev/hdb1** to create the file system.  However, when I do, the system generates: 

> /dev/hdb1: Invalid argument passed to ext2 library while setting up superblock

I have tried the following commands to do this step, and all of them give me the same error message:

mkfs.ext2 /dev/hdb1
mkfs -t ext2 -j /dev/hdb1
mke2fs -j /dev/hdb1
mkfs -t /dev/hdb1
mkfs -t ext2 /dev/hdb1
mkfs -t ext3 /dev/hdb1

So now I think I'm stuck.  Searching [www.google.com/linux](www.google.com/linux) for the error message yields little help, and I haven't found anything by searching these forums.  

So, can someone tell me how to make the file system on the new drive, or alternatively, is there a way to skip this step?

Thanks for your help.

---

### Post by kafton on 2005-02-14
> Quote:

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 24321 195358401 5 Extended 

I believe you have the wrong type of partition "5 Extended". That needs to be accessed with "/dev/hdb5". Or you could change the partition to type "83 Linux" with fdisk.

Ed

---

### Post by ryharv on 2005-02-14
Thanks for the help -- this worked until I restarted the computer.  Now, when I run *fs*, I get:

> ryan@HarvServer:/dev $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              7759252   1622624   5742480  23% /
tmpfs                   128468         0    128468   0% /dev/shm

No hdb1 is listed.  Any ideas? 

Also, once I get the hard drive set up, how do I write files to the new disk?  I am used to the windows world where each drive is represented by a letter.  Can I save files to any folder in the UNIX filesystem and have it allocate those bits to whichever drive it finds space on?

  ryan

---

