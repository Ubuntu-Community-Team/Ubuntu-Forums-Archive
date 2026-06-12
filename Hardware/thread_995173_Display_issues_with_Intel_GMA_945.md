---
title: "Display issues with Intel GMA 945"
date: 2008-11-27
forum: Hardware
---

### Post by MrJNewt on 2008-11-27
I have a crappy Gateway MT6705 that was running Vista until I got fed up with it and switched wholesale over to Ubuntu a few months ago. I'm currently running Intrepid. Unfortunately, I'm experiencing display issues which seem to be driver-related and I'm not sure how to go about resolving them.

Issue 1: Screen resolution problems. Back in Vista, my normal screen resolution was 1280x800. Ubuntu defaults to 1204x768 which makes things a bit fuzzy and chunky. Going to the Screen Resolution tool, 1280x800 is available, and when selected causes the display to become much sharper and crisp, but also badly misaligned to the left. That is, I can only see part of the desktop and a good quarter of the screen is black and dead.

Issue 2: I develop using SDL and OpenGL; frequently upon exiting one of my homebrewn programs, the desktop manager crashes and restarts. Checking the syslog, I find this line:
```
Nov 27 10:54:25 alcibiades gdm[5296]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```
These programs do not cause this behavior on my wife's computer (a higher-end Toshiba laptop with Hardy).

My understanding is that this laptop has the Intel onboard graphics unit, here's the first bit of my lspci printout:
```

ljustin@alcibiades:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

How can I ensure that I'm using the correct drivers (and what other things should I check) before I go and file bug reports?

---

### Post by MrJNewt on 2008-11-27
Well, as often happens, I have managed to fix issue 1 on my own. I went to Screen Resolution and upped the resolution. Then, when the screen went whacky, I used ctrl-alt-backspace to restart X. When it started back up, the screen was displaying properly and at the new resolution.

#2 is still open, though. It may be due to a stupid programming mistake on my part, but my apps generally run quite well on my work computer (a fairly beefy desktop with Intrepid), so I am still interested in making sure that I have the best drivers running. Can anyone give me a hand with that?

---

