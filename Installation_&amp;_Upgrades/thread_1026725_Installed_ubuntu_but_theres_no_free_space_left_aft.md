---
title: "Installed ubuntu but theres no free space left after install."
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by gravyplaya on 2008-12-31
I used the LiveCD to install Ubuntu next to my XP installation which I have done many times. Except when I checked to use the rest of the available free space for the Ubuntu install.  I selected 20gb of free space. I figured thats plenty as Ubuntu will use about 4 or 5gb and leave me 15gb free.. However this is not the case. Once I booted into my new ubuntu I looked at the free space and THERE WAS NONE.. Ubuntu installed using all 20 gb and left me no free space. Because of this I cant download anything and none of my settings stay because there is NO FREE SPACE.  Why did it install like that?  Have you ever seen ubuntu install and use all 20gb for it's installation? Now I cant use Ubuntu at all because theres NO free space for it. now I have a 20gb ubuntu partition/install I cant do anything with.

How do I fix this? Is there a fix? How do I just reinstall into the already made partitions? Is there a way to shrink the size of the installed ubuntu?

---

### Post by gravyplaya on 2008-12-31
BTW. I installed using a fresh Ubuntu 8.10 Intrepid LiveCD.

---

### Post by Just-trevor on 2008-12-31
You can resize the partitions by going to Synaptic Package Manager and searching for a partition manager.
Also, depending on how much free space you need, you can delete some programs you don't have any use for by going to add or remove programs
there are games and email clients and stuff like that that you usually don't need, and if you do need them, you can always just reinstall them.

If you run out of options you can just boot from the CD again and reinstall Ubuntu with a bigger partition

---

### Post by estyles on 2008-12-31
I don't think there's any way that Ubuntu is using 20 GB, assuming you didn't install a whole crap ton of programs and/or copy over a bunch of data to your /home directory.  It seems like something else is the problem.  (edit: Note "I think"...  there may be some crazy way that Ubuntu used up a whole 20 GB of space, not calling you a liar or anything...  but there's no way that should ever happen.  If checking disk usage and partition editor isn't helpful, I would recommend just reinstalling.)

I'm not on Ubuntu now, so I can't check, but there should be something like "Disk Usage Analyzer" in the main menu somewhere that should tell you where the disk space is.  Also, running the partition editor should show you your partitions and how much space is used on them - if possible, post a screenshot.  If not, let us know what it says...

---

### Post by gravyplaya on 2009-01-01
Thats just it.. This is a fresh install and I havent installed anything but the system updates. Partition manager shows 0mb available space on my / ubuntu partition.  Its like it literally used all free space for the OS.

---

### Post by estyles on 2009-01-01
okay, so did you try the disk usage analyzer thing?  it would help to know where the heck that 20GB of space is going to...

---

### Post by abn91c on 2009-01-01
try sudo apt-get autoremove
this will remove packages no longer used/needed, also uninstall junk programs you may never use like bluetooth, kopete, torrent, tape back up, news readers, etc...

---

### Post by gravyplaya on 2009-01-03
Ok so I think I figured out what happened..  I already have XP installed on this machine and when I was installing Ubuntu I had it import my documents folders and settings.. What I failed to realize is that I had gigs of music and other things in there.. So after it installed ubuntu it transferred over all that other stuff that I actually didnt need.. So I reinstalled without importing that stuff and everything was golden..  Those things dont need to be ported over because Ubuntu adds the other partition also.

I hope this will help out others so that they dont make the same mistake.

---

### Post by estyles on 2009-01-03
Aha!  Now that makes sense.  Glad you got it sorted out.  That's why I mentioned the Disk Usage Analyzer - it would have let us know that the giant sucking sound was coming from your /home directory.  That's also a good reason to keep /home on its own partition (but the installer doesn't really make that easy - you have to know what you're doing).

---

