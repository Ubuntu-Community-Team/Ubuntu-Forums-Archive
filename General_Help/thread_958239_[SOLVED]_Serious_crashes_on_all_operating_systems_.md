---
title: "[SOLVED] Serious crashes on all operating systems and livesessions"
date: 2008-10-25
forum: General Help
---

### Post by aomlives on 2008-10-25
Hi,

Since a few days ago I am experiencing serious crashes on my system. First Windows locked up completely to the point where I could only move my mouse but had to force shutdown using the PC button because I couldn't click on anything. After I rebooted this happened again after some time. I switched to Ubuntu so I could do stuff, but there I had the exact same thing! For the first time ever, Ubuntu locked up and in exactly the same way. Did force shutdown and went to Kubuntu install, and it happened there as well...

Sometimes the computer restarts of its own after it has been locked up for a while and then gives a BIOS warning of one long and two shorts beeps, which means the video display cannot be activated to display additional information. So then it restarts without the screen on so I can't see a thing... After I shutdown using the button it boots normal again.

I did a fresh Windows install, but have the same crashes: sometimes within minutes, sometimes it takes longer. I tried to recover my *ubuntu installs, but even my livesessions of both Gparted and Kubuntu 8.04 are crashing!!! I did a full RAM check and extended system scan at boot but got no errors...

Because it's on all OS'es the same I fear it's a hardware problem, but I have no idea what I should be looking for/which component could be the problem. Does anybody please have any suggestions to what could be wrong with my computer?

ps  this more or less started after I installed Windows XP SP3, but I doubt if this has anything to do with it

Many, many thanks for any help, it's greatly appreciated.

---

### Post by Kevbert on 2008-10-25
How did you perform a memory check ? Did you run memtest for a few passes ?
What happens if you remove/disconnect all non essential hardware (CD rom drives for instance) ?  Is the PC dusty inside try cleaning carefully with a vaccuum cleaner. Check all cards are seated correctly ?  How soon after boot-up does the PC lock-up ?  If it's a long time it could be an overheating problem.  What are your system specifications (including PSU rating) ?

---

### Post by schiznik on 2008-10-25
yep, sounds RAM related to me as well. Run memtest for a few passes, if you get any errors, remove a stick and run it again. repeat until you have found the bad stick(s)

btw, Kevbert you have some serious underclocking going on - running a Centrino at 1.6MHz... wow :confused:

---

### Post by Kevbert on 2008-10-25
> **schiznik said:**
> 
Kevbert you have some serious underclocking going on - running a Centrino at 1.6MHz... wow :confused:

Not really, it's just an old Acer Travelmate laptop.

---

### Post by aomlives on 2008-11-09
Sorry for the delay. I can now say for sure my computer is fine again.
I ran the memtest for quite a few passes, but this gave me no errors. So I cleaned out my PC like you said, removed all the dust even though there wasn't abnormally much. Yeah well, apparently there was because after I did this, everything worked again.

Thanks very much for your ideas and help.

---

