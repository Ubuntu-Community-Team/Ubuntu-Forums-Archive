---
title: "Configuring multiple hard drives"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by FooAtari on 2007-10-30
I am about to build a linux PC.

Currently I have a Vista PC with two hard drives.  One of the hard drives is comming out and going into the Linux box, it will be the hard drive I install Linux on to.  currently it is partitioned in two, one partition holds my music, documents pictures etc which I will be moving over to the Linux box. The second parition holds all my videos.

I have purchased a 500GB hard disc that I will be moving my video files over too.  So my original plan was to install the 500GB hard drive into the Vista PC and move all the video files over on to it.  I could then in effect use the empty 150GB parition to install linux onto and keep my music pictures and documents on the other parition and install both hard drives into the Linux box.  However that means I will need to format the 500GB hard drive into either NTFS or FAT32.

Also, it just occured to me that while I can format the empty partion on the 320GB hard drive (still with me here) in a linux file system, but that will still leave the second partion formatted in NTFS.

The only hard drive left uneffected in all of this is the hard disk that Vista is installed onto (which at the moment has 105GB free), which, when Im done will only have Vista and games installed, in effect making my Vista box nothing more than a games machine.

So what is the best way to go about this? I want to get from:

HDD 1 (in vista pc)

Part 1 - Docs/Musioc
Part 2 - Videos

HDD 2 Empty

to

HHD 1
Part 1 - Linux
Part 2 - Music/Docs

HDD 2 - Vids

All with file systems linux can work with nativly.

I also I have an 80GB hard drive I use for backing up, but could be wiped and used for other purposes during building the Linux machine.  Maybe Im seeing this more complex than it needs to be but right now it seems like hard work :)

I guess the easiest thing to do would be to maybe move all music and docs onto the 80GB hard drive or the empty space on the vista drive and then install Linux onto that partition.  Then once Linux is installed copy all my videos onto the 500GB disc which will now be formatted correctly.  I can then format the secod parition and copy everything over from the vista machine onto the 320GB hard drive.

Is there any point in having two individual paritions on the Linux PC (on the 320GB disk)? If I only had one drive for windows I would parition it and keep all my docs, pictures, music etc on it so if anything went drastically wrong with windows I could reformat the windows parition without loosing everything.  I guess that makes sense with any OS?

Anyway I thinks thats enough

Thanks so much for any advice!

---

### Post by dabl on 2007-10-30
Have you heard the story of the farmer with a duck, a fox, and a bag of corn, who had to get them across the river, but could only put 2 items in the boat at a time?

:lolflag:

I'm not even sure I understand everything I read there, but here's a concept for you, that might help you sort it out, if your new Linux box can hold 3 hard drives.

1. Make a GParted Live CD, by downloading and burning the ISO file from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

2. Put the new 500GB hard drive, that empty hdd from your Vista box ( I guess it's 320G?), AND your Vista hard drive all into the Linux box, boot GParted, and partition the 320GB drive (or the 500GB drive -- doesn't really matter) it into 4 primary partitions:

6GB  (future "/")
0.5GB (future "swap")
50GB (future "/home")
therestofit (future "/DATA_1")

3. Boot your Ubuntu Gutsy Alternate Install CD -- whichever version is for your new CPU.  Install Ubuntu, using "manual" partitioning.  The installer will "see" all three hard drives and all of their partitions.  Initially, all will show up as "/media/sdxx" designated drives.  Carefully select the partitions that you made for Linux, and highlight them, and then mark them to be mounted as shown above, and formatted ext3 (or swap, respectively).  Leave the rest of the partitions as-is.  The one I said could be "/DATA_1" could just as easily be left as /media/sdb3 or whatever it turns out to be, but it does need to be formatted ext3. The other empty drive needs formatted to a Linux filesystem format too.

4. When you reboot after installation, you'll need to install ntfs-3g to read the NTFS partitions. After doing that, you can copy at will.  When you're done copying stuff to your Linux system, you can shut down and remove the Vista drive and put it back where it came from.

5. Your Linux /etc/fstab file will need to be edited to comment out the no-longer-in-existence partitions that went back to Vista world.

How's that for a plan?  :lolflag:

---

### Post by FooAtari on 2007-10-30
Yes I guess the farmers problem is quite fitting :)  And I thought my post might be a bit messy...

At the moment the 320Gb drive in the Vista box inst empty.  Using GParted still might work though ill have a look, thanks.

---

### Post by lewisskinner on 2008-03-06
dabl's idea seems like a good one to me.  I'd set as follows:
6-10GB / (ext3)
50GB /home (ext3)
*Size of RAM* /Swap
*the rest* /shared (NTFS or fat32)

If using Ubuntu Gutsy, NTFS is now supported as standard, so no extra work is required!  I see you also have Mepis installed though (not sure if you plan on keeping it), I've no experience with Mepis, so I'm can't be sure if it supports NTFS nativly, but I'm sure you can download ntfs-3g

I assume gparted works with multiple drives too if you need.

---

