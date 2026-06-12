---
title: "Sanity check my partition scheme?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by endtime on 2009-04-23
Hey, before I start installing OSes, could you guys make sure my intended partition scheme makes sense?  I'm going to be dual booting Ubuntu and Windows 7 on a 640 GB drive.  I want to have separate /home and data/docs partitions for Ubuntu and Windows, respectively.  I have 4GB of RAM, so I guess that means I should leave 8GB for swap?

[Windows 7 - 30 GB - NTFS][Shared data - 567 GB - NTFS][/home - 20 GB - ext3][/ - 15 GB - ext3][swap - 8GB - ext3]

My intent is to keep everything I can on the shared partition, including Windows games, music, code, and documents.  Presumably version control systems etc. will run fine on Ubuntu if the code is on an NTFS partition?

---

### Post by nobodie on 2009-04-23
C drive for windows : usually installed first. I have heard that there can be problems with dualing W7 but I haven't tried.
D drive for W7 backup/restore files.
E drive for your NTFS file sharing. 

sda3 for /boot
sda5 for /
sda4 for 2 GB swap (you really will not need all that swap with 4 G RAM: swap was for when your RAM possibilities were very low and using the HDD made some sense for seldom accessed but still "on" procfesses: google "swap" and you'll find some discusssions of this question. Only in high use server environments is it recommended to follow the old 2X rule of thumb)
sda6 for /home

this entailed making sda 5&6 non-primary, but that makes little difference with linux (no requirement for anything other than /boot to be primary.)

This partition setup allows for easy upgrading, easy backup of data and OS in different locations (like data to a tape drive and OS to internal HDD location) and much easier if there are problems down the line.

Notes: 30 GB for W7, is that right????
12GB for / in ubuntu is enough. then, if your data is in the E drive you can reduce your home to 5 or 6 GB. 

Here is the Q though, why are you dualing when you could be using virtualbox? I run the latest VB and it lets me share the /home folder with Windows (as well as everything else that I want/need to share, run both computers simultaneously (no rebooting) and with 4 GB of RAM, run at native speeds and perform natively with everything I need to do. I suggest you try it before you leap, install it in ubuntu and see if you don't fall in love with the ease and utility of virtualbox, I have.Plus it has kept getting better.

---

### Post by endtime on 2009-04-23
> **nobodie said:**
> Here is the Q though, why are you dualing when you could be using virtualbox? I run the latest VB and it lets me share the /home folder with Windows (as well as everything else that I want/need to share, run both computers simultaneously (no rebooting) and with 4 GB of RAM, run at native speeds and perform natively with everything I need to do. I suggest you try it before you leap, install it in ubuntu and see if you don't fall in love with the ease and utility of virtualbox, I have.Plus it has kept getting better.

Is Virtualbox usable for gaming?

---

