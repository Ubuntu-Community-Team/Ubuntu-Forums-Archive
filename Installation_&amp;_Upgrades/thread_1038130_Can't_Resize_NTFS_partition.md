---
title: "Can't Resize NTFS partition?"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by greylander on 2009-01-12
Hello,  I'm trying to install Ibex (8.10) on a system with existing Vista installed.  My understaning was that in the partition step I would get the option to resize the existing ntfs partition to make room for the ubuntu partitions.  

Unfortunately the only "guided" optin I get is "Guided - Use entire disk".  

But if I choose "Manual", there is no option to resize.  When I "edit partition" there are only options fore file system type and mount point (and whether to reformat).  

Do I have to do the resize within Vista?  Would defragging in vista make a difference as to whether the resize option was offered?

Not sure if relevant, but the system I am installing to is an HP Pavillion laptop with 32 bit Vista (but a 64 bit intel processor).

---

### Post by damphoud on 2009-01-12
Yes, I believe you have to resize in Vista. Check out the link below.. pretty easy to do.
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by sendblink23 on 2009-01-12
Simply use  Gparted  *Its super easy*

With the LiveCD  head in the TOP MENU, then in System .. choose  Preferences or Administration,  not sure which but you should read Gparted in there.

Right there  you can do anything you want with any partition, just be quite careful not to Erase your current Vista partition.

Don't forget to save any backup of important files... to be secured on dvds or an external Hard drive.

---

### Post by greylander on 2009-01-12
Checking out gparted now... looks like it should do the trick.  Thanks!  If need be I'll fall back on resizing within vista (but I much prefer manhandling the vista partition with linux!).

I'm about to find out for myself, but I'm wondering whether gparted will have any problem shuffling the data around to fit into the new size, or if defragging will be a necessary step.

Also, any idea why gparted or something equivalent doesn't come up in the regular install process?  I seem to recall having the option to resize the existing OS partition when I installed Hardy Heron on another machine a while back.  And I'm pretty sure the install guide for 8.10 mentions resizing options in the partition step.

---

### Post by greylander on 2009-01-12
Looking for info on *gparted*, I've found out that resizing a Vista partition will make it unbootable (but can be fixed).  Perhaps the install detects vista and does not provide a resize option for this reason?

Here are some relevant links, for anyone else who encounters similar problems:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

May be slightly safer to do the resize within vista after all.  But I do so prefer to slap around that vista artition with linux tools.  LoL.

---

### Post by greylander on 2009-01-12
After reading comments in the first link above, it appears that depending on hardware, it may not be so easy to recover the vista partition and make it bootable after resizing with gparted.  Some of those comments are  year old, so maybe the latest gparted and latest vista will play nice together.  

I'm going to play it safe and use the vista partitioner.

---

