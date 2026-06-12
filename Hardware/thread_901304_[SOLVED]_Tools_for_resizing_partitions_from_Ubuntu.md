---
title: "[SOLVED] Tools for resizing partitions from Ubuntu"
date: 2008-08-26
forum: Hardware
---

### Post by silvanus2005 on 2008-08-26
I run Ubuntu and XP on a dual boot-machine. I need an application to resize the partitions from Ubuntu, because my XP is not working properly right now and I want to move data from XP to Ubuntu before reinstall XP. Any suggestions?

---

### Post by .nedberg on 2008-08-26
The tool you would use to resize a partition is GParted. I think you must install it first.

Are you going to resize your XP-partition and then move data from it? I would recommend that you don't do it that way! If your Ubuntu partition is large enough, just copy first, then resize. If it is not large enough then get some external storage!

Always backup data before changing partitions!

You can't resize a mounted partition, so using the LiveCD is recommended!

---

### Post by bankg3 on 2008-08-26
gparted? I would boot up with a live-cd and run gparted on your hard drive /dev/sda it should show you all partitions on your hard drive and you can edit move and everything else you want to do with them.  

becareful about changing the main ubuntu partition though, I would just create a new partition from part of your XP partition if that is what you are trying to do. I wouldn't resize the / partition, that might lead to some issues, I've never tried it though. Or borrow a friends external drive for a little while.

Did your XP quit working after the dual-boot installation?

---

### Post by silvanus2005 on 2008-08-26
Nope, my XP worked fine untill couple of days ago when I caught a virus. Since then, XP is not booting and I only can acces my XP partition from Ubuntu. Will this be a sign to completely switch to Ubuntu?:)

---

### Post by bankg3 on 2008-08-26
LOL, well good luck on getting back up and running

---

### Post by silvanus2005 on 2008-08-26
I made a backup of my data on several DVD, after that I made a fresh install of Ubuntu erasing my XP partition entirely. I can now say I am Windows-free:) I hope it will last a long time.

---

