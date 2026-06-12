---
title: "How to delete Karmic partition when reinstalling Jaunty?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by qwerty57 on 2009-11-09
I've got a bit of a problem.  I have dual boot Windows & ubuntu set up on my computer.  The Karmic upgrade just isn't working for me, so I'm reinstalling Jaunty from a live CD.  The problem I have is that I can't get rid of Karmic while going through the installation process.  I can shrink it down to less than 1/2 it's original size, but I just can't seem to delete it entirely during the installation process.  I don't want to choose the format everything option, because I need XP for work.  I don't need three operating systems on my computer, does anyone know how to delete Karmic so I can re-install Jaunty?

TIA.

---

### Post by 21ken on 2009-11-09
Install GParted in Jaunty and delete the Karmic partition from there.  If you want to integrate the hard drive space from Karmic into Jaunty, you'll have to resize the Jaunty partition.  This is all in gui, so it's easy to do.

---

### Post by darkod on 2009-11-09
I'm not sure I understand what you want to do but if you have all data backed up somewhere just format. You can keep the same partitioning providing you don't want to change that too.

Just select manual partitioning during Jaunty install, click on the (former) / partition and click Change button. Instead of Do not use select the filesystem, which would be ext3 probably, then check Format box and slect / for mount point.

Do the same for swap (no need to format so the option will not be given to you) and /home if you have it as separate partition.

That's it.

During troubleshooting last few days I replaced Ubuntu 8.04, Kubuntu 9.10 and Ubuntu 9.10 with each other just as above, no problems what so ever.

---

### Post by qwerty57 on 2009-11-09
Thanks,  I used gparted to delete Karmic & shrink Windows & then installed Jaunty from my CD.  Now all I have to do is copy my Docs, pictures and videos from my external HD and I'm set to go!:D

---

