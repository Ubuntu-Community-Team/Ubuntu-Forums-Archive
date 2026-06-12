---
title: "Gparted Help w/ live CD"
date: 2008-08-01
forum: General Help
---

### Post by Controls_Nut on 2008-08-01
Ok,

I have a System76 Serval Laptop ([www.system76.com](www.system76.com)) which I purchased a few months ago. I wanted to dual boot it w/ windows, so I found some tutorials, downloaded the Ubuntu 64bit ISO, and started going through the tutorials. 

Installing Windows XP was an Epic Failure, but I don't care about dual booting now, I just want the 30GB I partitioned off back (No data recovery required, just want to move the unallocated 30Gigs back on to sda3, which does have data).

Problem: The partition program (gparted?) while booted off the CD pauses every 5-15 seconds while trying to apply the resize. It will "unpause" if I move the mouse (touchpad), only to pause another 5-15 seconds later.

Suggestions?

---

### Post by Controls_Nut on 2008-08-01
Bump!

I have an official ubuntu 5.04 cd, could I try using that, or would it not be able to format the disk correctly?

---

### Post by dentaku65 on 2008-08-01
I suggest to use Knoppix live cd
[http://www.knoppix.net/get.php]("http://www.knoppix.net/get.php")
and boot with it.
Please be aware that in the live cd the partition swap (if exist) is mounted, so before to format with gparted you have to unlock that partition (with gparted itself)

---

