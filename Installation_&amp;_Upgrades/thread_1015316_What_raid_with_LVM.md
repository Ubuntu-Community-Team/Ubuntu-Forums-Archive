---
title: "What raid with LVM"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2008-12-18
I have 3 TB's of HD's (6 HD's total) and I want to setup a raid to protect my video files.  I have a problem currently managing disk space across mutilpe drives.  I would like to just copy and remove files without knowing how much disk space is available per drive. (Problem copying files across network to a disk drive and 10 minutes later being informed that there is now enough disk space) I would like to copy movies to a movie folder, pics to a pic folder, mp3 to a mp3 folder, etc without knowing how much space is available for that perticular file type.

Would setting a raid up and using LVM accomplish that?

What type of raid?  (0+1, 5, etc.)

PS. And what is MDADM?

I want to be able to copy files to my HD's without concern to what the available space on a certain drive is.

Kinda like a virtaul drive array.  Whether it be 3 1TB drives or 4 500 GB drives.  Any info would be greatly appreciated.

---

### Post by dwoods99 on 2008-12-30
Maybe [this will help]("http://blog.tklee.org/2008/11/moving-to-soft-raid-5-on-linux.html") get you started.

I managed to get LVM installed on top of RAID5 with 6x 1TB drives (4.55 TB useable).

---

