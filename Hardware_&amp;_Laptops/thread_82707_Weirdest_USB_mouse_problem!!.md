---
title: "Weirdest USB mouse problem!!"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by rasbach on 2005-10-27
Here's a weird one for you:

I have a system with removable hard drives, one for XP and one for Kubuntu (Breezy).  Since I have gone to the removable hard drive setup, whenever I am using XP I sometimes lose functionality with my USB wireless mouse (no other USB devices seem to be affected) and to correct this problem I have to shutdown my computer, remove the XP drive and put in the Kubuntu drive, start Kubuntu to the GDM- then shut down and put the XP drive back in (why bother- right?) And when I go back into XP my mouse is working great.  

I know what your thinking, restarting the computer is what fixed my problem-  wrong, I just restart it doesn't change anything- neither does a full shut down.  This is the strangest thing I have ever seen!  Can anyone explain this??  :confused: 

It should be noted that I never have any mouse problems in Kubuntu, Ubuntu, SUSe, or any other operating system.

FIC AU13 board  (uses Nvidia Nforce 2)
Removable Western Digital PATA drives @ 80GB each
512 DDR Kingston 
Athlon XP 2200 
Micro$ wireless mouse and keyboard (infared)

---

### Post by stuporglue on 2005-10-27
What if instead of just restarting Windows, you do a complete power off? I think when Windows does a restart, it doesnt' actually go all the way down. If that's the case, and the mouse status is one of the things that dosn't get re-read, that might be an explanation. 

Each time {K}Ubuntu starts up, it probes all devices to populate /dev, so the mouse gets a second chance to live. 

I'll bet if you power all the way off and unplug the mouse, plug in the mouse again, then start back into Windows, it'll work.

---

### Post by rasbach on 2005-10-27
Well, I said before that a complete shutdown didn't work either, I was thinking along the same lines as you.

I guess Micro$ peripherals are expected to be as buggy as their operating systems.  And as usual it takes Linux to get everything working right.  

So when there are Kubuntu brand wireless keyboards and mice, I'll place the first order. :D

---

