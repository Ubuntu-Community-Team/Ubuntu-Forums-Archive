---
title: "mounting/partitioning hd"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by trakie on 2006-07-07
Hey first off I'm new to ubuntu and think its great, I've not booted windows in about 3 days since having ubuntu for about 3 days. Anyway I have 3 hard drives installed (an 80GB partitioned at /dev/hda1 with windows on it, a 30GB partitioned at /dev/hdc1 for ubuntu in ext3 and /dev/hdc5 as swap.  These are fine, and I have another hard drive (250GB) that I tried to mount like I mounted my windows drive but rather than /media/windows i used /media/frank - this did not work, somehow I erased the disk by mistake (not a big deal I was planning on doing that anyway).  Anywho I am trying to format it now to be a huge ext3 file system to be shared between my windows and ubuntu setups.  I downloaded gparted and I tried using that, got an error whenever I tried to apply changes, then I tried through fdisk and I think I royally messed it all up.  If I go into disk manager I can see my 250gb hard drive and then click on partitions and I see:

Free Space
Partition 1
Free Space
Partition 2
Free Space
Partition 3
Free Space
Partition 4

for all the free space listings it says "Free Space, not partitioned" and "Size: 1024.1GB of free space not available"
for any partition # it says "Device: /dev/hss[#]" 
"Filesystem: Unknown" 
"Access Path: none" 
"Size: 1257.77GB (free space not abvailable)" 
"Status: Inaccessible" with an "Enable" button next to this, which when clicked nothing happens.  

Alright so I've looked around and I can't find anything to try because I've tried most things half way and was wondering if there was any way to fix this mess I made?  Thank you for any help, or pointing me in the right direction.  Another thing I just noticed, under storage list it lists a floppy which I don't have and clicking on that reveals properties that it is my 250GB hard drive at /dev/hdd.  I'm so confused right now.

---

### Post by Sonofmoog on 2006-07-07
From what you've written, there is no saving that 250 GB HD.  Delete everything and start again.  If GParted was no help, I'd download qtparted, and have a look with it.  I find it "fussy" sometimes, but it has saved my bacon any number of times when nothing else worked.  

Also, Ubuntu comes with partitioning tools cfdisk and sfdisk as well.  I've not used either, but if invoked without arguments, cfdisk loads in interactive mode, so you can at least look around .. 

My next suggestion is a possible <gulp> Windows solution.  Load your XP setup disk like you're going to reinstall.  When it loads, press r to load the Recovery Console.  When prompted for a password, press Enter without entering one.  When it finds your Windows installation, press 1 to select it and press Enter.  Once you are in the Recovery Console, run Diskpart to load the Windows partitioner ..    

Finally, if you have Partition Magic, it will create ext2 filesystems.  Don't know if it supports ext3, and almost certain it does not support Reiser

---

### Post by cracker on 2006-07-07
Well, it looks like your partition table is pretty messed up...I have a couple of options, if you can't get it working.

One idea to 'start over' is to zero the drive. To do this, enter the following command at a terminal:

 cat /dev/zero > /dev/hda

Where hda is the hard drive you want to erase. _**Make sure you use the correct drive!**_ Don't specify a partition number, just use /dev/hda if your drive is hda, etc.

Once this is complete, the drive should be completely empty, unformatted, unpartitioned, ready for you to set up. You will have to create partitions. I use fdisk, but there are numerous utilities. After you have created your partition(s), you will need to format them. To format them ext3, enter the following command:

mke2fs -j /dev/hda1

Where hda1 is your drive and partition. The -j option enables journaling, which is what makes it an ext3 partition rather than an ext2. There are other things that it adds and does differently, but that's very technical and beyond this scope--the point is, the -j option will make it ext3 instead of ext2.

---

