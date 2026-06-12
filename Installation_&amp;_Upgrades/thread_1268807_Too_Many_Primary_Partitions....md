---
title: "Too Many Primary Partitions..."
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Footbag on 2009-09-17
I'm working on getting a a dual boot Vista/Ubuntu system running and during the Ubuntu install I got a "Too many Primary partitions" message.   Vista is already installed, and the computer is partitioned from the factory.  One recovery partition.

In Vistas Disk Management tool, I see the Local Disk C:, a recovery partition D:, a EISA partition and the 100GB I have unallocated for the Ubuntu install.  

In Ubuntu's Gparted, I get a bit more info on the partitions, but am not quite sure what to do.  

I'm assuming I have the max number of Primary's, but don't know how to get rid of one.  I do not need the recovery partition, and could probably kill that.  That said, I know very little about partitions, and don't want to mess anything up.  Please help, dual boot is the only way I get to play with Ubuntu at work.

---

### Post by oldos2er on 2009-09-17
Linux will install to and run from an extended logical partition just fine. When the partitioner starts up during installation, choose manual, and you should be able to create an extended logical partition from the 100GB space you've already created.

---

### Post by Footbag on 2009-09-17
So I should select manual, then just highlight the "free space"? It tells me no root file system is defined.

---

### Post by solitaire on 2009-09-17
when you select the free space it will ask you how you would like it formatted (ext3, ext4 and the like!) there should be a bit to select between a primary or extended partition.

Select Extended and it will go away for a second or 2.It will then let you to create up to 4 more Primary partitions within the Extended partition.

So here's your drive: = 
|<-primary1->|<-primary2->|<-primary3->|[U]|<-----------120Gb Free space---------->|
[/U]
You then create an extended partition: = 
|<-primary1->|<-primary2->|<-primary3->|_|<------120Gb Extended partition------->|_

Then fill it with up to 4 primary partitions (Swap is a primary partition too.)
|<-primary1->|<-primary2->|<-primary3->|_|<|<-primary4>|<primary5>|<swap>|>|_


*OK* 
So i'm really bored so i thought I'd do the little diagram above! lol
^__^

---

### Post by solitaire on 2009-09-17
*Side note* 

You CAN have more than 4 primary partitions on a drive but only 4 will be seen!

I nearly borked my laptop when Win7's drive manager decided to take the 2 Ubuntu primary partitions in an extended partition OUT of the extended bit and make them normal partitions for some reason!!

So i ended up with 5 Primary partitions and could only see 4 of them! had to do a lot of playing and swapping about in the "TestDisk" program to recover the hidden partition and get data off of it!

Once I had the data i needed, i wiped the entire drive and started from scratch!

---

### Post by raymondh on 2009-09-17
> **Footbag said:**
> I'm working on getting a a dual boot Vista/Ubuntu system running and during the Ubuntu install I got a "Too many Primary partitions" message.   Vista is already installed, and the computer is partitioned from the factory.  One recovery partition.

In Vistas Disk Management tool, I see the Local Disk C:, a recovery partition D:, a EISA partition and the 100GB I have unallocated for the Ubuntu install.  

In Ubuntu's Gparted, I get a bit more info on the partitions, but am not quite sure what to do.  

I'm assuming I have the max number of Primary's, but don't know how to get rid of one.  I do not need the recovery partition, and could probably kill that.  That said, I know very little about partitions, and don't want to mess anything up.  Please help, dual boot is the only way I get to play with Ubuntu at work.

Check the manual to see if the recovery partition is required ALONG with the recovery CD.  Some OEM's require so. I suggest to leave it there unless TRULY not required.

As mentioned, convert the 100GB to an extended.  Ubuntu does not care whether it be logical (inside an extended) or primary.

With so much space, you might want to consider separating root from /home.  This means, you will have to create 3 logical partitions inside the extended (root, /home, swap).  Root is OK with about 15GB.  Swap is ok at about 2GB.  The rest for /home.

Post back if you need a tutorial/clarification.  Back up your files first.

---

### Post by Footbag on 2009-09-17
> **solitaire said:**
> when you select the free space it will ask you how you would like it formatted (ext3, ext4 and the like!) there should be a bit to select between a primary or extended partition.

Select Extended and it will go away for a second or 2.It will then let you to create up to 4 more Primary partitions within the Extended partition.

So here's your drive: = 
|<-primary1->|<-primary2->|<-primary3->|[U]|<-----------120Gb Free space---------->|
[/U]
You then create an extended partition: = 
|<-primary1->|<-primary2->|<-primary3->|_|<------120Gb Extended partition------->|_

Then fill it with up to 4 primary partitions (Swap is a primary partition too.)
|<-primary1->|<-primary2->|<-primary3->|_|<|<-primary4>|<primary5>|<swap>|>|_


*OK* 
So i'm really bored so i thought I'd do the little diagram above! lol
^__^

I get that error message as soon as I click next...  Nowhere to select between partition types.  Can I do it in either the Gparted or windows, or only in the Ubuntu install?

Edit...   The Edit partition option is greyed out for this partition.

Thanks for the help!

---

### Post by solitaire on 2009-09-17
Might be a long shot but make sure you're hard drive is not mounded when you try and install Ubuntu.

I assume you are using the LiveCD... Think their are problems when using the partition manager when the drive is mounted.

---

### Post by Footbag on 2009-09-17
OK, now something changed and the partition is showing up differently.  If I first click "use largest continuous space..." It's now labeled /dev/sda4/  :ext3.  But when I click next, it says I haven't specified a swap partition.  It says I should go back and do this.

IT isn't seeming to label the drive until it errors out while looking for the largest continuous free space.  Don't know whether to trust it, or where to go from here.

---

### Post by solitaire on 2009-09-17
You have to select "manual" instead of "use largest continuous space"
Then you create the Extended partition the a partition for swap and one or more for Ubuntu...

---

### Post by Footbag on 2009-09-17
> **solitaire said:**
> You have to select "manual" instead of "use largest continuous space"
Then you create the Extended partition the a partition for swap and one or more for Ubuntu...

Thanks for all of the help Solitaire...

When I create the extended partition, I highlight the free space, and then click new partition.  It lets me chose a size, location, and then has a drop-down with the options EX2, EX3, EX4, ..., SWAP, etc...  

Is this where I set the Swap and and extended options?  Sorry, I have never worked with partitions in the past.

Which dropdown option should be for extended?

---

### Post by solitaire on 2009-09-17
There should be an option for Extended or Primary partition above all the format type...

---

### Post by Footbag on 2009-09-17
> **solitaire said:**
> There should be an option for Extended or Primary partition above all the format type...

Nope, I went into Gparted as well and extended is greyed out.  The only option is primary.

Unless extended is one of the EXT#'s.  Is that the case?

And it looks like there is already an extended partition in the recovery partition.  Which might be what's pushing me higher then 4 primaries.

---

### Post by Footbag on 2009-09-17
I'm completely stuck.  Here is a screenshot of Gparted. 

[IMG]http://i288.photobucket.com/albums/ll175/Footbag01/scrpart.jpg[/IMG]

 I'm now wondering if I can eliminate one of the other partitions and use that space.  Perhaps the recovery partition.  I'm not sure if anyone can make a suggestion as to which way to preceed.

---

### Post by solitaire on 2009-09-17
right click on the unallocated space.
Select "New"
There should be a "Create As:" drop down option.

If not the only thing it might be is the location on the drive..
Move /dev/sda3 (and /dev/sda5) to the end of the drive and use the unformatted space in the current extended partition near the start of the drive

---

### Post by raymondh on 2009-09-17
> **Footbag said:**
> I'm completely stuck.  Here is a screenshot of Gparted. 

[IMG]http://i288.photobucket.com/albums/ll175/Footbag01/scrpart.jpg[/IMG]

 I'm now wondering if I can eliminate one of the other partitions and use that space.  Perhaps the recovery partition.  I'm not sure if anyone can make a suggestion as to which way to preceed.

The rule is 4 primary partitions or .... 3 primary + 1 extended.

From your screenshot, you already have an extended which contains sda5 (image back-up). Wish we had seen it (the screenshot) earlier ;)

Ubuntu needs at minimum (for a default install) at least 2 partitions (root and SWAP) hence the earlier suggestion to make it within an extended partition.  The problem is that you only have 1 primary partition left.  

it is not mandatory to have a swap partition.  It is recommended for 2 reasons .... your current RAM situation vis-a-vis your app usage and, your hibernation practices.

If you insist on having swap, then you have to give-up on something..  Looking at your recovery partition at only 1.5GB, I think those 2 (image and recovery .... sda5 and sda1) go hand in hand so be careful in choosing that.  You can try to get space from the 19.3GB extended to make and mount as swap but ... I do not know how that will affect your vista recovery capabilities.

Question :

1.  Do you have a original installation disc or just the recovery disc supplied by the manufacturer?  I ask because another option is to re-do the whole install.

---

### Post by Footbag on 2009-09-17
I do have the original disk, and could do a reinstall, but was trying not to.  Does that look like my best option considering the partitions the OEM made?

---

### Post by raymondh on 2009-09-17
As I see it (and open for further review by the forum), here are options:

1.  Make the 97GB a primary for Ubuntu root.  No more separating /home.  Consider making a swap file instead of a swap partition.  As it says, a swap file is a file.  See the [SWAP FAQ]("https://help.ubuntu.com/community/SwapFaq") to verify my information

2.  Make the 97GB a primary for Ubuntu root.  Create some space inside the current extended (about 1-2GB) and mount it as swap (linux swap file system)

3.  Re-do with intentions of creating a 

windows recovery - primary (if you insist) and in NTFS
windows - primary, NTFS for windows file system
Extended to house 3 logical partitions
- Ubuntu root
- Ubuntu /home
- Ubuntu swap
Data partition - to be shared by both OS', also primary and in NTFS

Again ... back up your personal files.  Also, make sure you have a installation disc (with key) instead of a recovery disc.  

If you wish, wait a moment for another poster to verify or provide a second opinion.

There's another option .... use the recovery 1.5GB as your swap.  But, I have a hunch that the recovery partition and the image-backup partition go together (i.e. one won't work without the other).

---

### Post by Bartender on 2009-09-17
What kind of computer is this?  Please tell me so I know what not to buy. 
I think the manufacturers are intentionally trying to tie up the partitioning so that the user can't do anything with it.

What a crock -  a little tiny extended partition at the front of the drive where you can't get to it.

I'm wondering if this manufacturer uses the RECOVERY area to run the recovery program, and that program then uses the data in the ImageBackup partition?  Or what??

I'll cautiously second raymondhenson's suggestion.  I say cautiously because I don't know how your recovery system works.  My Acer 5920 came with 4 primary partitions.  &%#$@)!  I made recovery discs, then I screwed up Vista so it wouldn't boot, then I ran the recovery discs.  The recovery discs wiped out three of the four primary partitions.  There was just one big vista C: drive.  

Installing Ubuntu was easy after that!

---

### Post by Footbag on 2009-09-17
It's a Systemax, and I just E-mailed them asking what my options are for removing the partitions.

I'd really love not to reinstall Vista.  I just got it running well.

---

### Post by raymondh on 2009-09-17
> **Footbag said:**
> It's a Systemax, and I just E-mailed them asking what my options are for removing the partitions.

I'd really love not to reinstall Vista.  I just got it running well.

Footbag,

If you DO have a installation disc (and not a recovery disc), then you can decide whether you want the recovery and image back-up partitions or not.  

If you decide so, seems to me you can delete sda1, sda5 and sda2 (in that order).  That'll free up about 20GB ... good for root (/) and swap.  Afterwards, I would convert the remaining 97GB into a DATA partition to be accessed by both OS'.

This advice assumes you have

1.  A install disc with a product key (just in case Vista borks on you)
2.  You don't care for the recovery or image-back-up

---

### Post by Footbag on 2009-09-17
Quick response from Systemax...

> 
    [FONT=&quot]Hello Adam,[/FONT]
   
  [FONT=&quot]Removing the partitions will not cause any problems, you simply will not be able to restore the image of how we shipped it. In terms of recovery you would need to reinstall the operating system from the ground up.[/FONT]
   
  [FONT=&quot]Regards,[/FONT]
   
  [FONT=&quot]-Ben, Systemax Tech Support[/FONT]
  

    

OK...  So I'm assuming that that means I can just flat out delete the partitions in either Vista or Ubuntu's partition editors, correct?

Thanks for the help all! And thanks for excusing the  noob questions.  I fresh installed Ubuntu on my older home desktop, and love it.  I'm trying to find a way to incorporate it into my work network, but will have to trickle it up.  I've actually got two of the same Systemax PC's that I'll be dual booting, both with the same partition problem, and two older PC's with fresh installs.

---

### Post by raymondh on 2009-09-17
> **Footbag said:**
> Quick response from Systemax...

  

OK...  So I'm assuming that that means I can just flat out delete the partitions in either Vista or Ubuntu's partition editors, correct?


As previously posted, using either Vista or gparted, delete sda1, sda5 and then sda2.  That will leave you with about 20GB unallocated to install Ubuntu on.  

Do you want swap?  Do you want to create partitions beforehand and then install unto them ... or do you want to do it during actual install?

As for the 97GB, you can make it your data partition.

---

### Post by Footbag on 2009-09-17
> **raymondhenson said:**
> As previously posted, using either Vista or gparted, delete sda1, sda5 and then sda2.  That will leave you with about 20GB unallocated to install Ubuntu on.  

Do you want swap?  Do you want to create partitions beforehand and then install unto them ... or do you want to do it during actual install?

As for the 97GB, you can make it your data partition.


Thanks, 
I'm home from work now, but will give that a shot tomorrow.  I will probably use a swap, as it seems to be optimal.  Does it matter whether I do the partitioning in Vista or Ubuntu?  Before or during installation?   Gparted seems a bit smarter then the other tools,  and I'd probably rather do it in that.

---

### Post by raymondh on 2009-09-17
> **Footbag said:**
> Thanks, 
I'm home from work now, but will give that a shot tomorrow.  I will probably use a swap, as it seems to be optimal.  Does it matter whether I do the partitioning in Vista or Ubuntu?  Before or during installation?   Gparted seems a bit smarter then the other tools,  and I'd probably rather do it in that.

Very well ... here's a brief guide.  You may already know how so pls. don't feel offended.

We're going to use gparted and will be in live session (from the liveCD)

After deleting, you'll be left with unallocated space about 20GB.

1.  Rt. click on windows partition to unmount it (just to be sure).

2.  Left clk on unallocated space (the 20GB you just freed) to highlight.  Go to PARTITION tab and select NEW. Select EXTENDED and make it use all free space.  select APPLY to make the extended partition.

3.  Click inside the newly created extended partition.  We will make 2 logical partitions (remember ... partition > New).

4.  make a linux Swap partition.  2GB is OK.  Format Linux Swap file system.

5.  make a ext3 (or ext4, if you wish) partition and make it use all remaining space.  This will be for root (/).

6.  When done, quit gparted and start the installer .

7.  In step 4, choose MANUAL

8.  Select the swap partition ... click on EDIT (button below) .... select USE .... and SWAP type

9.  Select the ext3 partition .... EDIT .... USE ..... EXT3 ... and / type

Proceed with the install. Review in step 7.

Now, if you insist/prefer to have a separate /home ... which comes to value if you have to reinstall ubuntu in the future hence making you retain your original config, user settings and files .... we have to do something different.  I suggest that if the space allocated is less than 30GB, its' best to have /home within root.  That's just my preference.  You can create a separate /home as part of the original 20GB you freed up.  

swap - 2GB
root - 8GB
/home - 10 GB

If so, then instead of creating just 2 logicals, you now create 3.  When install time comes around, just mount the appropriate / .... /home ... swap in their respective partitions.

Hope this helps.  Back-up first.  Good luck, Adam.

Raymond

---

### Post by Footbag on 2009-09-18
It works! 

Had some time to practice on an older laptop late last night.  Got it to dual boot, but made a few paritition mistakes. Knew not to repeat them this morning, and was up in a heartbeat.  

Thanks again all!

---

### Post by raymondh on 2009-09-18
> **Footbag said:**
> It works! 

Had some time to practice on an older laptop late last night.  Got it to dual boot, but made a few paritition mistakes. Knew not to repeat them this morning, and was up in a heartbeat.  

Thanks again all!

Excellent news.  Congratulations and happy ubuntu-ing.

PS.  remember to make your data partition NTFS.  ubuntu can read/write from/to NTFS.

Raymond

---

