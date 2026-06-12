---
title: "I have no clue what happened with my install"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by guine on 2009-08-22
The previous setup that I had for my computer was I had breezy on my first hard drive and feisty on my second hard drive, which was the install that I worked off of.  I tried to install jaunty over breezy on my first hard drive, leaving the second one alone so that I could copy my files over afterwards.  When I did the install it got most of the way through before an error about copying a file popped up and it said installation failed.  However when I look at my hard drives through the installer it thinks I now have jaunty installed on my first hard drive, but when I boot up in grub only my old setup of breezy on my first hard drive and feisty on my second show up.  Currently the only install that I can boot is feisty(without internet working) and when I boot it first sends me to a full screen terminal where if I enter shutdown -r now it will take me to the gui log in for feisty.  If I go back to the installer now to try to install jaunty on my first hard drive it wants to make me format my second hard drive as well as part of the process.  Does anyone have any clue what could be going on and how I can fix this?

---

### Post by VMC on 2009-08-22
Try the manual or custom install of the hard drive. Then use only the first hard drive. Assuming sda1. Can you get a list of hard drives "fdisk -l" using the livecd?

---

### Post by Hendrixski on 2009-08-22
in the future, you can use the advanced install to set up your /home/ directory as a separate partition.  That way you can install multiple distributions or even multiple versions simultaneously and each of them share your /home/ directory (meaning your apps would have all the same configurations and your files would be saved there so they are the same no matter which one you boot into).

---

### Post by guine on 2009-08-22
Ok, I'm trying the manual partition method.  This is how my hard drives show up in the partition manager.
Device        Type     Mount point     Format      Size
/dev/sda
  /dev/sda1   ext3                                 78477 MB
  /dev/sda5   swap                                 1521 MB
/dev/sdb
  /dev/sdb1   reiserfs                             78452 MB
  /dev/sdb5   swap                                 1546 MB

sda1 was my breezy install that is now showing up as having 9.04 and sdb1 has my feisty install.  I want to install 9.04 on sda1 while leaving feisty on sdb1 so that I can still boot that if something goes wrong.  I have everything that I want to keep copied off of sda1 so to install 9.04 there will I just want to select that one to format and set the mount point as /
And if I do that will I have to do anything so that sdb1 mounts automatically when I boot off of sda1?

---

