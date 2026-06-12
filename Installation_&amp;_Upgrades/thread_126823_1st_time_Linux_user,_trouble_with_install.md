---
title: "1st time Linux user, trouble with install"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by roncg41677 on 2006-02-07
I'm currently running XP Home on my work machine, which I wanted to make a dual boot and give Linux a shot. I downloaded the install disc, and when I try to install it it locks up on an "a" prompt with the following prefix: [DR-DOS]. A little further up on the screen it says something about not finding a FAT32 partition. 

My question is do I have to partition the drive first? I thought the install program would give me that option. If I do need to is there free software that will partition my C drive?

Thanks a lot! Looking forward to getting started with Linux!;)

---

### Post by Robgould on 2006-02-07
I think you can partition from the Ubuntu set-up but I never have.  I always make room from windows first then install to the free space.  i only do this because I am more comfortable with it.  I have partition magic.
 
As far as a free tool...how about ubuntu live CD?  I have never re-sized windows from Linux, but it is my understanding you can.
 
If you have more than one partition on your hard drive and are running XP you can modify the non-system partition from within XP.  It is part of the operating system.
 
You could also look at download.com and download a trial or shareware for a single use.

---

### Post by beameup on 2006-02-07
Sounds like you booted up into the restore partition of your hard drive.

Couple of things to look at:

Is your PC set to "boot from CD" first in the BIOS?

if it is then the download or the CD itself may be corrupted.

---

### Post by Sutekh on 2006-02-07
If you want some awesome installation guide, with plenty of pictures and explanations, including how to partition your drive (the install CD *will* do this),  you should check out **Herman's** Ubuntu install guides
                
[Install Ubuntu + NTFS]("http://users.bigpond.net.au/hermanzone/p3.htm")

[Install Ubuntu + FAT32]("http://users.bigpond.net.au/hermanzone/p2.htm")

---

### Post by roncg41677 on 2006-02-07
The install guides were a great read! I didn't even get the Ubuntu logo, so I'm assuming I may have a bad download? I ordered the free CD's, but they'll still be a few weeks. I may try to download again before that.

I am still very new to Linux, and am not familiar with how I would "resize Windows" from the Live CD. I tried the Live CD first, but didn't see anything related to partitioning.

I was also wondering if I need to worry about losing Windows data when I create a new partition? If I understood, I WILL NOT have to reinstall Windows, correct? 

Thanks so much for the quick responses! I'll update this thread when something changes.

---

### Post by roncg41677 on 2006-02-07
Oh, and yes, the CD is first or second on my boot up. The floppy drive may be first, I'm not sure at the moment.

---

### Post by Sutekh on 2006-02-07
[QUOTE=roncg41677]The install guides were a great read! I didn't even get the Ubuntu logo, so I'm assuming I may have a bad download? I ordered the free CD's, but they'll still be a few weeks. I may try to download again before that.
[/QUOTE]As a matter of interest, how did you burn the CD?  What program did you use? And what method?  It is important that the install disc is burnt as an **image** and not simply as data.

> 
I am still very new to Linux, and am not familiar with how I would "resize Windows" from the Live CD. I tried the Live CD first, but didn't see anything related to partitioning.To resize the windows partition using the Live CD will require using the program GParted.  You can look some more into it if you wish, though I'm pretty sure that the installation CD should do the trick for you.> 
I was also wondering if I need to worry about losing Windows data when I create a new partition? If I understood, I WILL NOT have to reinstall Windows, correct? 

Thanks so much for the quick responses! I'll update this thread when something changes.
If the partition goes smoothly then there is no need to re-install Windows.  I personally have not had to do any resizing, so it would be worth getting some opinions on how to resize windows partitions and any issues involved.

---

### Post by Sutekh on 2006-02-07
[QUOTE=roncg41677]Oh, and yes, the CD is first or second on my boot up. The floppy drive may be first, I'm not sure at the moment.[/QUOTE]
So long as the CD is before any HDD that should work fine.

---

### Post by roncg41677 on 2006-02-08
I used Nero 6, and I believe I did just burn it as a data disc. The only other options are music or video CD's.:-k

---

### Post by Sutekh on 2006-02-08
Ok that's why.  You *must* burn as an image.

[HowTo: Burn an ISO disc image with Nero in Windows]("http://www.ubuntuforums.org/showthread.php?t=111589&highlight=burn+nero+image") is a simple howto if you use Nero Express, similar if you use full Nero.  

Close the wizard at start-up and choose 'Recorder' and then 'Burn Image', then select the ISO you downloaded.

---

### Post by roncg41677 on 2006-02-08
Thanks Sutekh! That did it! 

Unfortunately, I don't have time to install today :(. Will probably have to wait for next week.

---

