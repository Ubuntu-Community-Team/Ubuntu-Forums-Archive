---
title: "80GB drive being reported as 32GB"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by andrewski on 2006-08-27
I just installed Ubuntu on a desktop computer with three IDE hard drives therein.  One of them, an 80GB drive, is being incorrectly reported as 23.62GB.  GParted showed no partitions thereon when I first put the drive in, and even after formatting it showed the same.

I've seen drives that have 32GB cap jumper selections, but this isn't one of them.  Any ideas what could be going on?  Any more info I could provide?

---

### Post by John.Michael.Kane on 2006-08-27
andrewski mind posting what brand/kind of drives they are?

---

### Post by andrewski on 2006-08-27
> **SD-Plissken said:**
> andrewski mind posting what brand/kind of drives they are?
The drive in question is a Western Digital WD800.  Let me know if the other drives' info would be useful and I'll post them too.

---

### Post by John.Michael.Kane on 2006-08-27
andrewski this is a drastic mesure.but can you unhook all the other hdd's but this one,and set it as master? then use the[gparted-livecd.php]("http://gparted.sourceforge.net/livecd.php") ,and see it can see full amount. 

also are there any sata hard drives in your machine?

---

### Post by andrewski on 2006-08-27
> **SD-Plissken said:**
> andrewski this is a drastic mesure.but can you unhook all the other hdd's but this one,and set it as master? then use the[gparted-livecd.php]("http://gparted.sourceforge.net/livecd.php") ,and see it can see full amount. 

also are there any sata hard drives in your machine?
Does it make a difference that the BIOS reports the drive as being 80GB?

And no, no SATA devices.

Edit: I took plugged in this hard drive and my CD drive on separate IDE controllers and booted up the Ubuntu Dapper LiveCD.  (Sorry, downloading something else is too much work. :p)  It's being reported correctly now.  What does that mean?

---

### Post by andrewski on 2006-08-28
> **SD-Plissken said:**
> andrewski this is a drastic mesure.but can you unhook all the other hdd's but this one,and set it as master? then use the[gparted-livecd.php]("http://gparted.sourceforge.net/livecd.php") ,and see it can see full amount. 

also are there any sata hard drives in your machine?
OK, I got it working.  Apparently, switching to the jumpers on the master and slave drives to cable select did the trick.  I owe my coworker a beer. :)

---

