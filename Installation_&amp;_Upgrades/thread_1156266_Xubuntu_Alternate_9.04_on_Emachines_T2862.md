---
title: "Xubuntu Alternate 9.04 on Emachines T2862"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by interestinfellow on 2009-05-11
Ok here's my problem.

Emachine T2862, Celeron D 2.66 ghz, 256 mb ram, 60 gb hdd, onboard video, basic PC.  It was running XP just fine.

Just installed Xubuntu 9.04, alternate install, and everything went well.  Rebooted, still good.
Xubuntu splash screen shows, the bar runs back and forth, and then fills up (like it should) and then the screen goes blank (like it should), and then I can't do anything.  The screen just stays blank, no cursor, no gui/logon, no nothing.

Anyone?

Thanks.

EDIT: I have been looking around and only saw one unanswered post relating to this situation (they had the same problem).  Please help.

---

### Post by dstew on 2009-05-11
Possibly this is due to a video display driver (kernel module) that is incompatible with your hardware. After the screen goes blank, wait a while and try ctrl-alt-F1. If that gives you a command-line interface, that suggests it is a display driver problem, and not a bad OS install. Or, try booting into Recovery Mode.

---

### Post by interestinfellow on 2009-05-17
esc during grub, second boot option (safe mode/recovery), fix graphics problem, clean boot, fixed.

Thanks.

---

### Post by Georgesl on 2010-03-14
Could you tell this newbie how you fixed the graphics problem?  I've just been gifted the exact same computer and I'd like to try Karmic on it.

EDIT:
Never mind.  Just opened the computer and smelled the tell-tale aroma of electronic smoke.  Turned out that this model of e-machine has a habit of blowing its power supply and taking the motherboard with it.  Great quality contol, that.  Ah, well, at least I got a couple of good hard drives out of it.

---

