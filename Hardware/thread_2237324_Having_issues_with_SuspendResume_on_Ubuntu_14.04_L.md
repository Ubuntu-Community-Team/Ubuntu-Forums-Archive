---
title: "Having issues with Suspend/Resume on Ubuntu 14.04 LTS"
date: 2014-08-01
forum: Hardware
---

### Post by Mason_Fultz on 2014-08-01
I have a Gateway T-6330u and I'm running a dual boot system with Windows 7. I'm having an issue where my laptop won't resume from suspend. The screen stays black. I don't remember having this problem prior to this version of Ubuntu, I had BackTrack 5 on here before. Any help would be great, just let me know what you guys need from me. Not extremely new to Linux or Ubuntu, but I'm rusty when it comes to both, so whatever you give me for help, have mercy and use little words lol. 

Thanks guys, 

Mason

---

### Post by Mason_Fultz on 2014-08-01
Oh, and I also can't control the brightness of my screen.

---

### Post by keithspg on 2014-08-01
Probably need more information. I am also having a similar this issue. My first intel graphics subsystem. I installed xubuntu 14.04 and noted a lot of messages in the dmesg related to i915. I installed gnome-session and stuff including gdm. At this point, if I suspend, it resumes to a dead computer. Lights are lit, but it is not 'up'. Black screen and not present on the network (cannot ssh into it). I then wiped and reinstalled xubuntu 14.04. From this point, I could suspend and resume though the error was showing in dmesg. I filed a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324935](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324935) and subsequently an upstream kernel bug. The bug appeared in mainstream v3.6 something. 

I do not know what happened, but now, even with a clean xubuntu (no gnome) but fully updated, i still get dmesg filled with errors, but now it will not resume from suspend.

I am guessing I will need to cripple it by using nomodeset because the intel drivers are not completely functional with anything newer than 13.04?!?

---

### Post by Luser2 on 2014-12-02
FWIW, I'm also having this problem on this old Gateway laptop - AMD-64, hough, not Intel, and ATI Radeon graphics.  I _can_ control the brightness, and the system _seems_ to come back up (the various lights do their thing), but the screen remains black.  Clean install, fully updated.

---

