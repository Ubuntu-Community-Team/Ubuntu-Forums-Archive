---
title: "Quick Swap Dual Boot - Seems Theoretically Plausible..."
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Kitt22 on 2009-06-16
Hello! Let start off by saying that this is my first time posting on the Ubuntu forums, and I'm not entirely sure if this is the correct place to post my question. If it is not, would a Mod kindly move it to a more suitable subforum?

With that out of the way: What I would like to do is to install Ubuntu and Windows on two separate hard drives, and have a third hardrive for shared data between the two. Now this in itself isn't too challenging - the part I want to know about it on the fly switching between the two OSes.

In theory, how I figure this would work, is while running off of one harddrive, it would put the current OS in hibernation mode (some low resorce running mode), then boot the OS on the other harddrive. Switching back would, again, put the current OS in hibernation mode, then unhibernate the other OS. In this way, one could switch between the two OSes, without having to completely shut down then entire system and reboot. Currently open documents and programs could be left open, etc.

I've tried looking around for something like this, but to no avail. I was simply wondering if anyone on the Ubuntu forums knew of anything like this, or had any ideas of a way to impliment this, or even if such a thing is impossible.

Thanks in advance =)
--Kitt

---

### Post by u-slayer on 2009-06-17
Yes that works just fine. It will even work with with two OS on the same hard drive, but in different partitions. Understand that you can only switch between OS when you put the system into HIBERNATION (aka suspend to disk). Standby mode will not work.

However, everytime you want to switch, you will have to hibernate the current OS. Then boot your computer and select the other one. This will still take some time. If you are only using windows for a select few, non-gaming applications (Such as Office, Excel whatever). You may want to look into running a Virtual OS. Which you can switch to instantly.

---

### Post by Kitt22 on 2009-06-17
> **u-slayer said:**
> Yes that works just fine. It will even work with with two OS on the same hard drive, but in different partitions. Understand that you can only switch between OS when you put the system into HIBERNATION (aka suspend to disk). Standby mode will not work.

However, everytime you want to switch, you will have to hibernate the current OS. Then boot your computer and select the other one. This will still take some time. If you are only using windows for a select few, non-gaming applications (Such as Office, Excel whatever). You may want to look into running a Virtual OS. Which you can switch to instantly.

Interesting, so nothing additional needs to be installed. I mostly want to be able to do work related tasks under Ubunutu, while have windows available for gaming - but I was looking for a way to switch from gaming to non-gaming, without having to worry too much about closing out all of my other applications to do so. I'll do this method (once I've finished reinstalling windows and then Ubuntu) and report back here if I have any questions or concerns =)

---

