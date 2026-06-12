---
title: "Mode not supported in 9.10 fresh install"
date: 2009-12-07
forum: Hardware
---

### Post by spliner on 2009-12-07
Sorry if this has been asked in the past, but I'm having some issues installing 9.10.  I've tried both the regular and the alternate CD for installing and run into the same problem.  After install (only the alternate CD got me this far) the system reboots, grub loads, and after a few seconds of a blinking cursor I get "Mode not supported" on my monitor.  I assume it's because my monitor can't handle whatever resolution Ubu is trying to use as default, but how do I fix it?

I've been saving parts for this Ubuntu box for quite some time, all test good, here are my specs:

MSI K8T Neo-V motherboard
Sempron 2800+ processor
512mb RAM (have 2GB on order) DDR 400
Nvidia 7800 GT (EVGA 256mb) AGP 8x
160GB SATA 5400 RPM HD (Seagate)
8x DVD/CDRW SATA Drive
19" Wide Flat LCD (Can't remember what brand of the top of my head)

Anyone have tips?  I have been using Ubuntu since 7.04 so I'm not a total newb, but I am still new at diagnosing hardware/driver issues.  This is a fresh install, the HD is new and everything else is used, but tested good.  Just stuff I have laying around from upgrades.

---

### Post by Yellow Pasque on 2009-12-07
Have you tried the "safe graphics mode" option? Can you boot into a recovery console?

---

### Post by spliner on 2009-12-07
I have tried the safe VGA mode, but I have not tried the recovery console.  My guess is at this point I need to know how to change the default vga mode because it obviously can't be displayed by my monitor (640x480 or 800x600 maybe?).  My monitor supports resolutions up to 1440x900 but I don't think it supports terribly low resolutions.

I'll try the recovery console tonight, but unless I can get into a terminal of some sort I'm still kind of stuck.  I'll try CTL-ALT-F1 tonight and see if I can at least get that opened.  Otherwise I'll have to search the garage for an old monitor lol.  Surely there's a more simple method of changing the default resolution without having to be in the desktop?

---

### Post by spliner on 2009-12-14
Turns out.. it may have been a bad vid card after all.  I had only previously tested it on an Ubuntu Server system (IE: No GUI).  Loading it up into a Graphic mode at all bombs out.  I tossed it in a box to test later in a Windows system and tried an old card I had (non-3D piece o crap) and got the desktop to load just fine.  So it's either a driver issue with the nVidia 7800 GS CO (EVGA) or it is a bad card although that card was working with I pulled it a year ago and packaged it back up.  So for now, no nVidia goodness but at least my system is up and running.

Spliner

---

