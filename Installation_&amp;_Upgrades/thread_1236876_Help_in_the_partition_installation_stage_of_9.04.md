---
title: "Help in the partition installation stage of 9.04"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by mark_t on 2009-08-10
I am trying to install Ubuntu 9.04 on my laptop.  I have XP on it currently.  I want have the laptop to run duel.  My problem is when I get to the partition state of the installation I have 3 choices.
At the top it says no operating systems are on the drive
The 3 choices are:
1. install it side by side
2. use the complete disk  Note: it detects XP here
3. Manually
I don't want to take a chance manually.
I don't want to use up all the room so side by side might take all my space
And I don't want to dump XP.
Version 8.04 had a way to drag how much space you wanted to give Ubuntu but it appears 9.04 doesn't give that opportunity.
Can anyone tell me what to do.  I only want to use about 10 Gig until I can afford to buy a new machine.
Thanks

---

### Post by running_rabbit07 on 2009-08-10
I don't know what you use your system for but if you just want to get a good taste of Ubuntu you should do it manually. I can walk you through it. It is easier than it looks.

---

### Post by running_rabbit07 on 2009-08-10
Being that you only want to use ten gigs, go to manual mode. Click on your NTFS partition and make it smaller by 10 Gigs. 

Then you will be creating 2 new partitions. 

Partition 1 is going to be 1 gig. You will set it as a Swap Partition.

Partition 2 will use the rest of the space. set use as to EXT3. Set the mount scroller to " / "
If it asks whether you want primary or logical, choose logical.

Then you are ready to install. 

If you have not defragmented your XP, do so. Before you defrag, use disk cleanup to delete all temp folders. This will move all of your files to the front of the drive.

---

### Post by mark_t on 2009-08-10
Thanks.  When I looked at manual mode, it had about 4 different things there so I quit.  I didn't see anyway to make new partitions.  I had to quit to come here and ask.  I will copy your answer and try again.  Does that sound OK?

---

### Post by running_rabbit07 on 2009-08-10
> **mark_t said:**
> Thanks.  When I looked at manual mode, it had about 4 different things there so I quit.  I didn't see anyway to make new partitions.  I had to quit to come here and ask.  I will copy your answer and try again.  Does that sound OK?

Sure, you may have to right click on the partition.

---

### Post by mark_t on 2009-08-10
Thanks, I will try all this tomorrow.  The last time I install Linux was about 10 years ago and it was mandrake.  LOL  I had a rough time on the partitioning then too.  Come to think of it, I always have rough time partitioning.  Thanks again.

---

### Post by drs305 on 2009-08-10
mark_t,

Welcome to Ubuntu. Just a word of advice if you end up choosing the "side by side" option. There has been some confusion with the current installation process. If you select "side by side" in Step 4, you *must* adjust the Ubuntu partition size on the bar at the bottom of the choices. If you don't, you will end up with an Ubuntu partition of about 2.3Gb, which will be too small to work.

---

### Post by running_rabbit07 on 2009-08-10
> **drs305 said:**
> mark_t,

Welcome to Ubuntu. Just a word of advice if you end up choosing the "side by side" option. There has been some confusion with the current installation process. If you select "side by side" in Step 4, you *must* adjust the Ubuntu partition size on the bar at the bottom of the choices. If you don't, you will end up with an Ubuntu partition of about 2.3Gb, which will be too small to work.

+1 for that way. I have never did that method. Does it automatically make the swap?

---

### Post by mark_t on 2009-08-10
OK, I will try side by side tomorrow again.  Maybe the bar is after I hit forward from my choice.  I can always quit again or try manual.  Thanks again.

---

### Post by drs305 on 2009-08-10
> **mark_t said:**
> OK, I will try side by side tomorrow again.  Maybe the bar is after I hit forward from my choice.  I can always quit again or try manual.  Thanks again.

I have a graphic of Step 4 in the following post. It was written for people who had already installed and got a 2.3GB partition but it will work to prevent that as well.  ;-)

[How Did I End Up with a 2.5 GB Ubuntu Partition?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

For full disclosure, I have not used the "side by side" method - I've only dealt with users who have.

---

