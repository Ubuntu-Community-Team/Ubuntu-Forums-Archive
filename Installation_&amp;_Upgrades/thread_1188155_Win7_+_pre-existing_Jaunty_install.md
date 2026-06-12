---
title: "Win7 + pre-existing Jaunty install"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by BlokX on 2009-06-15
Just a quick rundown of the current setup:

I had 2 partitions on this HDD...one with XP 32-bit and one with Win7 64-bit.  XP was the first to be installed, followed by Win7, so it used Vista bootloader.

Then I decided to scrap Win7 (beta was gonna run out anyway) and install Ubuntu Jaunty 64-bit on here.  This overwrote the Vista loader with the Linux loader (Grub i'm assuming) and all is still well.

So, for all intents and purposes, at this point it's as if XP was installed first, then Ubuntu.

Now I want to use the Win7 RC, but I'm not giving up Ubuntu.  I love it and programming on the Linux platform is something fresh and new to me (avid Windows developer).  So I'm thinking about formatting the XP partition and putting Win7 64-bit there.  Will this mess up my boot loading or does Grub look for all possible boot partitions on each startup?  Basically I don't want Grub to lose the windows boot loader and me not be able to access it.

Thanks, and sorry if this was longwinded. Just didn't want to leave anything out.

---

### Post by zvacet on 2009-06-15
You can do that but you will have to [reinstall grub.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by BlokX on 2009-06-15
awesome!  thanks so much.

---

