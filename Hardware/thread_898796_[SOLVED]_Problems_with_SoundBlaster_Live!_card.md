---
title: "[SOLVED] Problems with SoundBlaster Live! card"
date: 2008-08-23
forum: Hardware
---

### Post by sergentsiler on 2008-08-23
before anyone complains if this has been here i did search and i only found a solution for a different SB Live! card and it was for and x86 machiene.

my problem is this, i cant get any sound to come out of my SB Live! CT4780 card on my Dell Precision Workstation 340. i have checked the sound properties and it looks to be enabled in the preferences if i right click to get to them. but if i go to System>Preferences>Sound, it is enabled for my "Default Mixer Track" but not for sound playback for sound events, music/movies, or audio confrencing neither is it enabled for sound capture. and when i go to the pull down boxes, only my intel integrated is listed. 

i need to find out how to install the driver for my card and desperately because the built in dell speaker aint cutting it :D

any help would be nice

---

### Post by libra1780 on 2008-08-24
the driver you need is EMU10K1_Audigy
post your dmesg and lsmod to see if the driver tries to load
type them in your console

---

### Post by sergentsiler on 2008-08-24
thanks but one of my friends suggested switching everything to multichannel output and that worked.

---

