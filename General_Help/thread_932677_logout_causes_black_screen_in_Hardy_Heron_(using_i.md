---
title: "logout causes black screen in Hardy Heron (using i810 chipset)"
date: 2008-09-28
forum: General Help
---

### Post by IanVonSpeedfreak on 2008-09-28
Okay, so I know there are loads of threads like these on the forum, problem is they each seem to be dealing strictly with nVidia or ATI chipsets and I'm using an older Pentium Celeron Gateway that uses intel graphics (w/shared memory).  I've used Dapper, Feisty, & Gutsy and I can't recall having this problem with any of those versions. I'm using a clean install, and have only installed updates and multimedia codecs (via the stickied Comprehensive HowTo).

Initially my desktop resolution was set to 1280x1024@60Hz, but I changed it to 1024x768 because 1280x1024 is too much for eyes (everything's too small).  I'm making note of this because I've noticed that after I logout (or rather, *attempt* to logout) my monitor reads that it is reset to 1280x1024.  I tried fixing the black screen logout problem by changing the virtual resolution in usplash.conf, and while my monitor readout on logout did indeed change to 1024x768, the screen is still black and no matter how long I wait, stays that way.  I had everything reset by using the recovery mode, but the problem persists.

I have a feeling this whole problem relates to Hardy Heron's sole usage of autodetection in preference to editing of the xorg.conf file.  If that's the problem, is there any recommendation against actually replacing the xorg.conf file with one from an older version's liveCD (e.g. I have a working Kubuntu Feisty Fawn CD)?

BTW. here's the specs for computer:
**Monitor-**
Goldstar Studioworks 57i
**Tower-**
Gateway 310s
Intel Celeron 2.4Ghz
Intel graphics
Intel sound
**Keyboard-**
standard US Gateway (came with computer) with no multimeda or other additional functions (PS/2)
Microsoft Basic Optical Mouse 1.0a (USB)

Also, I'm having a more minor issue with my keyboard.  For some reason, numlock is working in reverse (numbers work when light is off, page up, page down, etc. work when light is on).  WTF is going on?

---

### Post by IanVonSpeedfreak on 2008-09-28
bump

---

### Post by IanVonSpeedfreak on 2008-09-29
Okay, so this is what I've been able to figure out so far, with xserver-xorg-video-vesa installed, logout goes black.  So I figured I would install the more specific xserver-xorg-video-intel driver and things would work better, wrong, with the intel driver installed, logout worked, but the resolution went fubar (for some reason widescreen resolutions were enabled, and the 1024x768 option was unavailable) and performance was sluggish (as compared to having the vesa driver installed).  Now with both installed, logout functions properly and haven't encountered any performance issues.  So, while things may "just work", I'd like to know if anyone can provide a possible explanation to how this is working.

BTW. What happened to the post-login splash screen the other versions of Ubuntu had?

---

