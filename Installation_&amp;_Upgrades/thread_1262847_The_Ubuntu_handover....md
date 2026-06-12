---
title: "The Ubuntu handover..."
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by TheGingerNija on 2009-09-10
I currently have a dual boot machine with Windows Xp & Ubuntu 9 (XP kind of being 'in charge').
 
However after a few weeks playing with, learning (& messing up a few times) I've found myself booting into Ubuntu more & now that I've tried a few ideas I'm thinking of switching the machine over to Ubuntu as in swap my NTFS drives to EXT3 or 4 & removing windows.
 
Before I make the big switch over though I'd like some advice.... the partioning of my drives (13gig & 120gig) & mounting, I'm thinking;
 
/boot  = 200 MB
swap = 2GB
/ = 11GB
/usr = 20GB
/home  = the rest
 
Any advice would be helpfull before I switch tomorrow night (or tonight if theres nothing good on TV)

---

### Post by ajgreeny on 2009-09-10
Seems OK, but why a separate /usr partition?

If there is a good reason, carry on as you suggest, but most users are very happy with /usr just being part of the root partition.  In fact most users also have /boot as part of root, as well, but perhaps in advance of ubuntu 9.10, there may be a reason to have it separate, just in case the ext4 file system messes things up in any way.

---

