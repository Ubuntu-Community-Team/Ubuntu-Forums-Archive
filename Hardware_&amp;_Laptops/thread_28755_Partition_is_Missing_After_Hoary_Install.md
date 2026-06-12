---
title: "Partition is Missing After Hoary Install"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by sandmanfvr on 2005-04-21
Ok I have an 80 gig hdd partitioned:

60 gig for main windows/apps/games
10 gig for files like drivers, mp3, movies, etc.
10 gig for dvd ripping/burning.  also good for converting video to dvd


Well I decided to install Ubuntu on the dvd partition.  I did the install, it went fine.  Bootmanager installed fine and I could boot into XP and into Ubuntu.  When I go into My Computer in Windows, the main 60 gig partition is there, the 10 gig dvd partition is there (now called linux), but my other partition is nowhere to be found.  Man, have so MANY things on there like pictures and such.  I got a data recovery tool that I know should get the data back, but this is irritating.  I don't understand what happened.  Any suggestions?  I NEED that data (about 3 gigs of stuff).  Thanks.

Oh, I got an external 20 gig hdd and I plan to move the stuff to it after this.  I love Ubuntu, just need to connect to AOL.  :confused:

---

### Post by heimo on 2005-04-21
On windows, go to diskmanager (diskmgr.msc I think) and check if the partition is visible, but haven't been assigned with drive letter. That kind of thing has happened to me earlier, but not because of any Linux distribution.

On Linux side, do fdisk -l /dev/hda (or what-ever the device is) to check if the partition is listed as should. Try mounting it on Linux. When you get access, copy the stuff to another partition and get a backup. (I guess that was unneccessary to tell...)

Don't do anything that is irrevers.. irreversib.. anything that you can't reverse. :D

---

### Post by sandmanfvr on 2005-04-21
Thanks.  I will have to try one of these.  I just want the data off of that partition.  Got some things that can't be replaced.

EDIT: How do I run diskmanager?  Do I have to go into the windows directory to run diskmgr.msc?  Thanks.

EDIT2:  Found it.  Duh.  ](*,)   Any help on dialing up to AOL?

---

