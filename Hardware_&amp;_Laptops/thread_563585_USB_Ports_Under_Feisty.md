---
title: "USB Ports Under Feisty"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by justinmiller87 on 2007-09-30
I have an IBM Thinkpad R40 with two USB 2.0 ports on it. My system dual-boots with XP and Feisty. In XP, my ports are recognized as USB 1.1 (an odd thing if you ask me, but for an entirely different forum) and in Feisty, they don't even work at all. When they were working, they would load my external drives, but would then unmount them without any warning, usually in the middle of doing something, but not always. I thought this might be a hardware error (the laptop has been in Iraq for ten months now), but it doesn't seem like it is. If anyone has any suggestions for me, please let me know.

Thanks a bunch.

Justin

---

### Post by justinmiller87 on 2007-10-01
Bump #1

---

### Post by justinmiller87 on 2007-10-06
I'm going to go ahead and bump this one last time. Thanks.

---

### Post by Sigmund on 2007-11-04
> **justinmiller87 said:**
> I have an IBM Thinkpad R40 with two USB 2.0 ports on it. My system dual-boots with XP and Feisty. In XP, my ports are recognized as USB 1.1 (an odd thing if you ask me, but for an entirely different forum) and in Feisty, they don't even work at all. When they were working, they would load my external drives, but would then unmount them without any warning, usually in the middle of doing something, but not always. I thought this might be a hardware error (the laptop has been in Iraq for ten months now), but it doesn't seem like it is. If anyone has any suggestions for me, please let me know.

Thanks a bunch.

Justin

Bad news.

I have a ThinkPad R40 that I bought used.  It also started unmounting drives at seemingly random times.  First with stuff that pulled a lot of power, then even little flash drives.  Sometimes I would get a warning about the ports being low speed (1.1) and sometimes they would work at 2.0 speeds. The problem came up in XP, and I actually used Knoppix to check if it was a software issue, but the drives didn't work in that either.  

I've read some through some ThinkPad forums and lists, and this appears to be a fairly common problem with R40s.  Some people report that this is a preliminary issue and eventually more ports (PCMCIA, VGA etc) will stop working.  My USB ports failed entirely almost a year ago, but nothing else has stopped working.  They've also never, not even once started working again, and I check them regularly in XP and Ubuntu.

My solution was to order a USB 2.0 PC card from newegg.com.  You can pick them up for  10-15 bucks, I've gone through three because the cards stick out from the laptop and I'm too lazy to remove them before throwing the laptop in a bag.  The cards I buy from "Syba" seem to provide enough power to run a certain drives, but not all of them.  There is a power adapter spot to plug in your own power supply for full powered ports.

However my dead ThinkPad USB ports still provide full power (I checked them with a multimeter), they just don't communicate any more.  I got a special USB cable with an external hard drive case, and it looks like a Y.  You plug the lone end into the drive, plug one of the pair ends into your low power ports and the other into another port and it pulls power from two ports to supply full power to the drive.  I plug one into the PC card and one into a dead port and it works.  However it doesn't pull enough power if I plug both paired plugs into the PC card.

Give the PC cards a try and hopefully nothing else dies on your R40.
You can also mod them so they don't stick out, and hopefully last longer.
[http://kyndal.dk.googlepages.com/cutpcmciausb2card](http://kyndal.dk.googlepages.com/cutpcmciausb2card)
Or you can just be careful.

---

