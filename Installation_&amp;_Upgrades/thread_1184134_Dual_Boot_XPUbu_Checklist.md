---
title: "Dual Boot XP/Ubu Checklist"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Raharu on 2009-06-10
Hi everyone!  Earlier this week I started preparations to go from Windows Vista to an XP/Ubuntu configuration.  I believe I've got everything sorted out, but I figured I'd list everything I'm planning to do before I DBAN and find out it's too late.

Here's my plan so far:
-I've got all necessary files backed up
-I've got DBAN, XP, and Ubuntu 9.04 boot disks
-I've made a CD with video, network and mobo drivers for both systems in case something goes wrong.

1) DBAN my HDD and get Vista off 'a there.
2) Use XP's utilities to format my 150GB HDD into a 20GB Windows partition, 20GB / partition, 2GB /swap partition, and then I'll have 10GB left over for a /home, but I'm also making a 100GB "common" partition (in ntfs?) for both OS' to use.
3) Install XP.
4) Install Ubuntu.
5) Go back and put on essential drivers, and check that everything works.

I'm a little iffy about the partitions, does everything check out that way... or should I use Ubuntu to set up the linux partitions?  I'm not exactly sure how it needs to be done, and if /swap needs to be done a certain way.  Any help on that would be appreciated, and if anybody could tell me if something is glaringly wrong, I'd appreciate that too!

Thanks :)

---

### Post by Mark Phelps on 2009-06-10
I'd recommend using Ubuntu's utilities to format the Linux partitions.

Also, I'd swap the sizes for home and root.

---

### Post by merlinus on 2009-06-10
+ 1.

You might set up an extended partition for all but windows, as it will make creating separate partitions in the shared 100G easier down the road, should you choose to do so.

---

