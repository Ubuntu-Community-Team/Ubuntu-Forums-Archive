---
title: "Partitioning: option to use &quot;free space&quot; with XP"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by beesblaas on 2009-07-02
Dear Ubuntu friends/nerds/boffins:

I want to install Ubuntu 9.04 on a new system with XP for a dual boot.
It has only one 320Gb ntfs partition with XP on. I have defragmented it.

1)
I read in the link below for 9.04 in the section for Dual-Booting that I should use GParted to shrink the windows partition for XP.
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)
I dont understand why, because the installation disk has an option, see (2)

2)
the option "use the largest continuous free space".
There is a slide bar, I can move it to the left to increase Ubuntu size.
The slide bar stops at left at about 5.9 Gb. Is this the upper end of XP,
and can I assume anything to the right (e.g. 20Gb) wont destroy XP ?

3) If I put the slider at e.g. 20Gb, and proceed, what will I get?
will the installer re-size and create new partitions for / and /swap and /home?
Will I have a choice in how big they are?
What will they be, EXT3 ?

4) If I completed option 3 and install, and I boot into the XP, will XP sort out it's  shrinked size?


5) will Ubuntu  be able to read & write files  in the XP ntfs partition ?
(if not, I have to make a common  additional partition with fat32 ?)

ALTERNATIVES:
If option 2 does not give me much choice,
and I use the manual option, how do I shrink the XP partition safely?
I have sda1 size=320062Mb, used=6386Mb. 
Should I click on it, edit,
and choose  new part size e.g. 20000Mb and select "do not use the partition"?
and then divide the remainder in / and swap and /home ?

Thank you very much, I await your answers before I screw up anything.

---

### Post by x22 on 2009-07-02
you will find option 1) easier, that's why it's
recommended.  The installer fdisk is quite a blind
tool that permits massive screwups.  Use "gparted."

---

### Post by running_rabbit07 on 2009-07-02
Yes, using Gparted or if you already have a partitioner program in windows you can use it. I you set it up ahead of the install it will work better. Like the other guy said, the installer partitioner doesn't care what it deletes while making the new partition. 

Whichever way you decide to make the partition you can make it EXT3 or EXT4 and it will work fine, though there are a few people who have had issues with EXT4.

You can make your swap with the partitioner or with the installer, it doesn't matter which. Every time I let the installer do it, the swap was about 3 gigs. 

The latest install I completed on my PC I used EXT4 and did not create a swap, I will probably regret that one day but I think 2 gigs RAM will keep up just fine.

---

### Post by beesblaas on 2009-07-02
Thanks for the reply, I have now considered option 1, i.e. "side by side", but I'm not sure what this means, (what partitions will it then create ?)

I see that I can also use the slide bar for option-1, say I slide it to 20Gb for XP, how will it divide the rest? I would prefer to have my Ubuntu /home in a separate partition, then I dont need to worry about re-installations etc, it will be safe. Will it do that? How much will it allocate for my swap? 

Can someone who used the "side by side" option plse check how the installer divided the partitions?

thanks

---

### Post by beesblaas on 2009-07-02
thanks Running_rabbit07 for your answer as well.
I will check out Gparted tomorrow, will let you know how it goes.

Whatever option I use,
I still need to know if ubuntu can read & write to the XP ntfs partition,
because if it cannot do that reliably, I want to create a common fat32 partition as well.

---

### Post by running_rabbit07 on 2009-07-02
I have previously used that way of installing and it did work fine. The swap will be between 500MB and 3GB. Depending on the size RAM you have and the things you plan to do with your system is how you figure if you need more. If you just surf the net and load your MP3 player and such you don't need any more than 2 or 3 GB swap. If you edit and create DVDs and such then you will need more.

I have installed Xubuntu and Ubuntu several times on this system and an old laptop I have and never had any problems. The install package was very well built and should set you up fine. 20 Gigs should be plenty enough for Ubuntu to work being I have Ubuntu with all my music and Gigabytes of Images and videos and I haven't even used 20gigs yet.

Hope this helps and good luck. Let us know how it works for you.

---

### Post by running_rabbit07 on 2009-07-02
> **beesblaas said:**
> thanks Running_rabbit07 for your answer as well.
I will check out Gparted tomorrow, will let you know how it goes.

Whatever option I use,
I still need to know if ubuntu can read & write to the XP ntfs partition,
because if it cannot do that reliably, I want to create a common fat32 partition as well.

It can read the NTFS and it will most likely create an EXT3 partition unless you tell it to do EXT4. There are other formats that Linux can use but I know nothing about them.

---

### Post by raymondh on 2009-07-02
Hello and welcome.

First, some links for reading and reference.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Have you backed-up your files?  Pls. do so.

I have found that you need to give XP some breathing room ... and have settled at 40GB.  Your requirements may vary.

Your preference to create a common storage partition is also viable.... and the common format will be NTSF.  This partition is separate from XP and Ubuntu and both will be able access that partition.  Likewise, you may also create a separate /home.

In effect .... your HD will have 3 MAIN partitions. XP (primary), Ubuntu (extended) and Storage (primary, NTSF).  Of course, you have to decide on how much size you wish to allocate to **XP**, **UBUNTU** and  **STORAGE**.

Should you decide to do this you need to:

1.    Resize XP to your prefered size.  I prefere to use windows' own disk management tool to resize a windows partition.  Once done, quit and close the windows tool.

EDIT : aack ...I forgot you were using XP and its' disk management tool will NOT resize down.  You'll have to use gparted or your favorite partitioning tool. I will use gparted. 

_Remember to REVIEW before clicking APPLY._

2.    On the unallocated/free space, create 2 partitions (for Ubuntu and Storage).  

2.a.  left Click on unallocated space > partition menu > new > make EXTENDED > set desired total size for Ubuntu > apply *(this will be your ubuntu install)*
2.b.  Click inside the newly created extended partition to make 3 partitions.  You have to decide whether to use EXT3 or EXT4.  I will use ext3 for this example.

-  Make a linux SWAP partition about 1.5GB and format LINUX SWAP FILE system
-  Make a 15GB partition and format EXT3 *(this will be where ubuntu root (/) will reside)*
-  Make the last one EXT3 as well and use remaining space inside that extended partition.  *(this will be for /home)*

3.  After creating the partition for ubuntu, left click on the remaining unallocated/free space > partition menu > new > primary > use all space > format NTSF. This will be your **STORAGE**.

After all the partitions are created, quit and close gparted.

On to the installer ... 

When you get to the partitioning stage, choose **MANUAL**

1.  Select the Swap partition and click EDIT PARTITION (button below), *set* it to **USE** and *file type* **SWAP**
2.  Select the 15GB partition > EDIT PARTITION > '**USE**' ; '**EXT3**' ; *type* '**/**'  
3.  repeat for the last partition (the one for /home) > edit > **USE** ; **EXT3** ; **/home**

Continue with the install.  Once done, check by booting both XP and Ubuntu.  If all is OK, do update ubuntu first.  

We'll work on mounting the STORAGE partition after everything boots well and OK.

Hope this helps.  Post back if you need clarification on this scheme and/or further assistance.

More links for reference

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)      (thanks herman!)

Good luck.

---

### Post by beesblaas on 2009-07-03
Thank you all!
 I have followed the steps as Raymondhanson described. Everything worked fine. I just have a few additional notes. 

a) I downloaded and burnt a bootable GParted CD.  

b) I then booted GParted and used it to shrink the XP partition   

c) I then booted XP, in order for XP to fix up its shrinked partition. XP has no problem with this, on the first boot it detects its shrunk partition, runs CHKDSK by itself and thereafter suggests a restart. After restart it says "windows has finished installing new devices". 

d) I then booted from the Ubuntu instal disk, and followed the procedure as described by Raymondhanson.    

Note that if your disk has only one partition, then GParted shows a bar which represents the entire disk. There is a slider on the bar which you can slide to the left to shrink the disk, but this is not evident. The slider looks like the right-hand edge of the bar. Just go to the right-side edge and move it to the left.    

When I actioned gparted to shrink the XP partition, I had a bit of a scare, it reported "move /dev/sda1 to the right and shrink it from 298 Gib to 40 GiB". However it did not move it to the "right", it just shrank it to the left, as expected.   

Also, as you allocate the partition sizes, there is a small discrepancy between the chosen size and actual size. e.g. if you select 10 GiB, it might end up 9.8 or something. I found this rather annoying. I know there are rounding errors and a difference between 1M =1024 and 1M =1000, but why not be consistent, or indicate sectors, as SUSE partitioner does/did?    

I used type ext3 for linux and I made my communual/shared disk partition type fat32, but, as mentioned above, seems like Ubuntu has no problem writing to NTSF partitions. I might re-format it to NTSF again. 

Many thanks to all. Now I have to do a similar thing on my Vista laptop.

---

### Post by running_rabbit07 on 2009-07-03
I am sure many will agree it is much nicer to help someone do their homework before the install than to help fix the mistakes from doing it without them understanding how to do it correctly.

Thanks for adding in how it worked for you. That may be all it takes for someone else to read and install it correctly.:guitar:

---

