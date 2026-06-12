---
title: "Help me switch!"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by thecrumb on 2006-02-15
I finally got a laptop for work so I  no longer need Windows on my home PC so I want to install Ubuntu! 

I've downloaded the Live CD but so far have not gotten far.  I've run about a zillion command line options and so far this seems to get me the farthest into the boot process:

% live irqpoll nolapic nocddma

or 

% live irqpoll nolapic nodma nocddma

Both of these go through almost the entire start process - usually hanging after I see "starting hotplug subsystem" or "calculating module dependencies"

My system:

CPU: Intel P4 3.0Ghz
Mobo:  Soyo SY-P4I875P "Platinum Ed" 
Drive - Maxtor 80GB SATA
DVD/CDROM: Plextor PX-708A
RAM: 1GB 
Video: ATI Radeon 9800 Pro All-In-Wonder

Help me switch!  I know ATI video support isn't the best - would a different video card work? 

I've also re-downloaded the ISO and burned it a second time (at 4x) thinking it might have been a bad CD but no difference.  

Any other ideas?

Jim

---

### Post by Robgould on 2006-02-15
I have a laptop and ATI video card and p4 processor...all should work.  If you want to install to your hard drive, why did you download the live cd?  I have never installed from the live cd so I don't know about that, but if you download the regular iso, it should install no problem.

---

### Post by plexi50 on 2006-02-15
I have an almost identical system and the live CD boots with no options. What type of errors do you get? To install, the regular ISO would be a better choice, I am not sure how to install from the live cd or if you even can.

---

### Post by thecrumb on 2006-02-15
I basically tried the Live CD just to test to see if it would work with my hardware.  :)

With no additional install options - installation usually fails during the intial boot while it's detecting all the hardware. 

Jim

---

### Post by Robgould on 2006-02-17
If I had to guess, it is your sata drive that is giving trouble.  I would search the forum for that.  I can't see anything else that strikes me as a problem.  I might be wrong though.

---

