---
title: "XP/7 dual boot...want to swap 7 and Ubuntu"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by BlokX on 2009-06-06
I guess the titles sums it up.  I have XP and Windows 7 installed on the same hard drive, on seperate partitions.  It's a 250gb drive, 50gb partition is the Windows 7 partition.

When I booted up from the Ubuntu disk and got to the partition application, I tried to format the 50gb partition and I messed around with all of the options, but I couldn't figure out how to make Ubuntu replace the Windows 7 install.  The only "good" option was installing it at the end of my XP partition, which I do NOT want to mess with.

When I installed Windows 7 it used the vista boot loader.  Is this the problem?

How can I go about putting Ubuntu where Windows 7 currently resides?

thank you so much!

---

### Post by namd3r on 2009-06-06
Does it let you reformat the Windows 7 partition at all?  Or delete the Windows partition and install Ubuntu into the free space?

---

### Post by kennethadammiller on 2009-06-06
What I'm getting is that you want to replace windows seven? ok well, the option to install ubuntu on the largest free unformatted space is in the install preferences of ubuntu... just delete a large space whereever you want ubuntu to go and then go through the install process and choose on the largest free continuous space

---

### Post by kennethadammiller on 2009-06-06
Actually, let me rephrase all of that. Get gparted and delete the windows 7 partition. then just use it to slide the xp partition over. then delete the space where you want ubuntu to go. install ubuntu as described before

---

### Post by Elfy on 2009-06-06
You don't need to get gparted it is on the livecd - System Admin Partition Editor - start that - if you have only 2 partitions it will show them - delete the win7 partition then when you install choose the largest free space - it should see the 50GB and install it there. 

Obviously ask if you have more questions.

Not being at all sure about vista and win7 I would suggest making sure that you have the vista bootloader set up correctly before I removed the win7 - possibly use the vista dvd/cd to fix it's boot.

---

### Post by BlokX on 2009-06-06
Okay..here's the situation as of right now.

I'm currently running on the live CD.  I used GParted inside Ubuntu Live and deleted the 50gb Windows7 partition completely.  Now when I look at this hard drive i have about 200gb ntfs file system which XP is currently installed on, and i have about 50gb unused.  not formatted or anything.  it's where 7 used to be.

When i go to install Ubunto I tell it to use the largest continuous free space.  It then updates the bar at the bottom showing me that it's going to resize the windows partition to be about 240gb and install Ubuntu in an 8gb section at the very end.

I can drag the slider over to keep the XP partition at 200gb, but i'm concerned that this might cause some sort of format on that partition

Any help is appreciated.  You've helped a lot so far. :)

EDIT: just for more info, I managed to get the Vista boot loader off of my system.  I used the XP CD's recovery to remake the MBR.  Now my computer boots directly into the XP partition.  And still has ~50GB of unused, unformatted space.

---

### Post by Elfy on 2009-06-06
How about going for manual partitioning - the following will look worse than it actually is :)

First thing you need to decide is whether to have a seperate home - this means that if and when you to do a clean install rather than an upgrade your configs and personal stuff can be preserved.

Secondly - how much RAM you have and whether you have a need to hibernate or not needs to considered in relation to the size of your swap - this is similar to a windows pagefile.

If you need to hibernate then swap needs to equal RAM, with my 2Gb I have a 1Gb swap which very rarely gets touched and could be smaller - depends what you want to do.

So - open the Partition Editor in the Sys Admin menu - you should see the 50Gb space you got once win7 was gone - right click and create an extended partition to take all 50Gb. Right click once more - new - make a partition for swap, format to linux-swap - the size of this depends on your earlier decision. 

Now we can make the partitions for the install - if you decide not to have a seperate home then you can just make 1 partition to take the whole of the remaining space. If you are wanting to have home seperate then ... 

Right click inside the extended again - new - ext3 - 10Gb should be sufficient. Right click once more and create a new ext3 partition with the remaining space - this should be much larger.

You should now have 2 or 3 new partitions INSIDE the extended partition. This is half way there for the partitioning - start the installer - when you reach the partition stage - choose manual.

You can forget about swap now - it will be recognised. I am going to assume you have a seperate partition here - if you don;t forget the second part of the following.

Select the 10Gb partition - Edit partition (near the bottom) choose Ext3 from the drop down Use As menu and then choose / from the dropdown Mountpoint menu.

Select the larger partition - Edit partition (near the bottom) choose Ext3 from the drop down Use As menu and then choose /home from the dropdown Mountpoint menu.

Close that window and you will be back at the partition menu - the 2 new partitions will show that they now have mountpoints.

REsume with the rest of the install.

Don't do anything to your ntfs partitions at all. You can access them later once the install has finished.

---

### Post by BlokX on 2009-06-06
If I don't want a seperate HOME partition, do I set the mount point for the partition I'm putting Ubuntu on to / or to /home?

Thanks.

---

### Post by Elfy on 2009-06-06
> **BlokX said:**
> If I don't want a seperate HOME partition, do I set the mount point for the partition I'm putting Ubuntu on to / or to /home?

Thanks.

If that's the case you need to make one partition and mount it as /

---

### Post by BlokX on 2009-06-06
forestpixie, you're my hero.  I'm running Ubuntu now and it's great!

So now 1 final question before this thread can be considered done...

Now that I have it all installed, I failed to realize there is a 64 bit version of Ubuntu.  Not sure why I didn't look for it, it just slipped my mind.

Is it worth formatting this partition and going with the 64 bit version?

---

### Post by Elfy on 2009-06-07
> **BlokX said:**
> forestpixie, you're my hero.  I'm running Ubuntu now and it's great!

So now 1 final question before this thread can be considered done...

Now that I have it all installed, I failed to realize there is a 64 bit version of Ubuntu.  Not sure why I didn't look for it, it just slipped my mind.

Is it worth formatting this partition and going with the 64 bit version?
:lol:

I just did exactly the same as that myself yesterday ;)

If you decide to do so you can just boot with the livecd - when you reach partition part - choose install.

For the / partition you do as before and make sure to tell it to format, for the /home tell it to use the right mountpoint but DON'T format.

When I first installed I reinstalled quite regularly as I mucked things up - why don't you wait and see how things go before deciding.

It is though up to you ...

---

