---
title: "Macbook (1,1), No Sound, Red Light"
date: 2011-08-03
forum: Hardware
---

### Post by shijinmodan on 2011-08-03
Okay, so my optical output light on my Macbook 1,1 is on. I'm running Ubuntu 10.04. I've tried gnome-alsamixer, and disabling IEC958, but when I play music it re-enables itself and will not disable. I've tried just using Alsa and disabling the S/PDIF (which I know is just the terminal equivalent of Gnome-Alsa, but I figured I'd give it a shot.) The same result. 
     I've tried the toothpick (with the power off) and resetting the optical sensor on the logic board.
:confused: 
I'm at my wits end.

EDIT:  Okay so I added:  "options snd-hda-intel model=mb55" at the end of my alsa-base.conf file located in "/etc/modprobe.d/alsa-base.conf"

After adding that line (even though I know my Macbook is 1,1) and executing:  "rm -rf ~/.pulse" (which deleted the .pulse directory), I rebooted and VIOLA!, I have sound. It took me 3 weeks of respite, but it has been achieved. I hope this helps someone else out there with the same problems I had. 
:guitar:

---

