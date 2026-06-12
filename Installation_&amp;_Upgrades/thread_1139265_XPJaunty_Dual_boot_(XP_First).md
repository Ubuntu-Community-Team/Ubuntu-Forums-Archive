---
title: "XP/Jaunty Dual boot (XP First)"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Nathan Otis on 2009-04-26
In another thread I've detailed my issues with an upgrade from 8.10 to 9.04. I decided to try a clean install of Jaunty, and thought while I was at it, I would dual boot XP.

So I formatted the drive, installed XP and then set about trying to install Jaunty. The partitioner has changed from the last time I dual booted (probably around the dapper era). Gone is the easy to use "slider" which allowed one to make an existing Windows partition smaller. I'm not certain how to proceed.

Any tips?

---

### Post by BobbyS on 2009-04-27
I think it is easier to use gparted partitioner. Since you are at the new install point you can play around with it and not lose anything. Here is the link, take a look.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Nathan Otis on 2009-04-27
> **BobbyS said:**
> I think it is easier to use gparted partitioner.

BobbyS,

Thanks for the suggestion, but I have Gparted. I've used it before, but it doesn't seem like there's a way to shrink the existing NTFS partition while leaving the XP install intact.

Does the common wisdom say install Ubuntu first, or was I going about it the right way? Hindsight being 20/20, I should have partitioned a little more purposefully (which is probably what I'm going to end up doing tomorrow).

---

### Post by dubref on 2009-04-27
You are doing it right, XP first then Ubuntu.

99% sure that I used Gparted (from live Ubuntu CD) to shrink XPs NTFS partition 10GB  when I installed Ubuntu 7.10 a while ago on a laptop. 

Should be the same with 9.04, but if it isn't, I suppose one solution would be to use 7.10 live CD .... :P

---

### Post by Mark Phelps on 2009-04-27
Would recommend downloading, burning, and booting from the GParted LiveCD (which you can get from distrowatch.com).  That's the latest version and tends to be newer than the one bundled with the distros.

---

### Post by Grandon on 2009-04-27
Before you start the shrinking I would recommand you to defragment the HDD with the windows defragmenter utility.

Greetz,
GND

---

### Post by Nathan Otis on 2009-04-27
I went back to defrag the windows partition and for some reason, XP would boot. I decided then and there to reinstall XP, partition the drive during the install and just move forward.

I'm posting today from the fully functioning Ubuntu 9.04 install that I did immediately following.

There's a lot to be said for doing things right the first time.

Thanks all.

---

