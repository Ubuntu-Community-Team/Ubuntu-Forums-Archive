---
title: "Need help. Install Ubuntu NBR on netbook"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by xsivone on 2009-08-29
[B]I have an Asus 1005 and I am trying to install Ubuntu NBR as dual boot on it.  It has a 160GB hard drive that Asus split into two partitons, so putting Ubuntu on one partition makes sense.

Here is the problem that I am having.[/B]

When I got to where it is tells where to install, it said to install to the partition (that said it would erase windows XP) and below it says to manually set it up.  I chose manual since I do not want to install over Win XP.  When I did that it showed multiple partitions on the hard drive.  Two 74GB partitions, a 5GB, and a small one.  The first partition I believe has the Windows installed on it, so I chose the second one and clicked next. 
Then it said no root file system is defined.  What did I miss?


[B]I was told to delete the second partition so that it would turn into allocated space and Ubuntu would just install to it.
[/B]

I deleted the second partition.  Then I quit and rebooted and went into install again.  Nothing changed.

Now I am sitting in the same screen, I am looking at the following table

Device       Type     Mount Point    Format?   Size      Used
/dev/sda1    ntfs                              77375     7230
free space                                     77366     
/dev/sda3     fat                              5247      3760
/dev/sda4                                       49      unknown


At the bottom of the screen I am at step 4 of 7   I can Quit   or go Back or Forward
If I select forward a warning comes up saying   No root file system is defined.  Please correct this from the partitioning menu.
If I click on the free space I have an option for a new partition.  When I click that it asks primary or logical, then the size in megabytes, then the location beginning or end.  Then use as either Ext3 journaling file system, Ext4 journaling file system, Ext2 file system, ReiserFS journaling file system, JFS journaling file system, XFS journaling file system, FAT16, FAT#@, swap area, or do not use the partition.


**This is what I was told to do to make it work.**

Select free space and select new. Leave it as Primary Partition. Select Swap from File selector. Resize free space a little  to 1 gig for swap (you should still have a  big section of free space remaining and showing)and hit apply. Select end of Drive if asked.

After it is done. Select the rest of unknown space. Select New. Leave as primary partition. Select Ext3 file system. Hit apply. 

After it is done.

Select your new Ext 3 file system by right clicking on it. Select Label from the menu. In the open window that pops up type /. Just like in my screenshot  I gave you. After that you should have a / mark included in the line for your new EXT 3 file system. When done exit Gparted and point installer to whatever gparted named your new  Ext 3 file system. Write down its label if you need to /dev/sda/ (whatever). Just make sure you point NBR at /dev/sda/whatever and it should start the install process.

[B]I followed this advice.  This is what happened.
[/B]
As soon as I did the first paragraph about the swap partition, it rescanned the drive.
Now the remaining space is listed as unusable and I am unable to do anything with it.


I am getting frustrated.

---

### Post by stlsaint on 2009-08-29
please see signature below on [DualBooting]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by xsivone on 2009-08-29
I actually figured it out.  I was using Gparted in the install portion of Ubuntu and it was not deleting my partition.

What I figured out as to go into Ubuntu NBR live and do it there.
Then I rebooted and it worked fine.

---

