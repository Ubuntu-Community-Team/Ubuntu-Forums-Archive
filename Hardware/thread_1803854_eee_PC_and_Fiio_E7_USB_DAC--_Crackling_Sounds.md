---
title: "eee PC and Fiio E7 USB DAC-- Crackling Sounds"
date: 2011-07-13
forum: Hardware
---

### Post by Lrawrl on 2011-07-13
I have recently installed Ubuntu 10.10 on my eee PC 1201ha (I couldn't find working graphics drivers for 11.04). When I tried playing music from my Fiio E7, I heard terrible crackling sounds mixed-in with the audio. Just to make sure it had nothing to do with the audio format, I tested FLAC, mp3, wma, youtube videos-all had the same crackling sounds. 

I suspected that my audio device may had very low latency, so I installed the Mediubuntu repository and added the plugins for low latency devices-still heard crackling. TBH, I'm not even sure if this would help, anyway.
 
I admit that I know very little about Ubuntu or the way PC's handle external sound cards, but my only solution is to blame this ill-performance on the crappy hardware inside my computer and ditch the USB DAC, for now. Does anyone have any ideas on what the crackling sounds are? Is this problem fixable? Any input would be greatly appreciated.

(I asked this same question on head-fi and didn't get much help, yet)

---

### Post by AlKi on 2011-09-12
hm, i've got the same model (1201HA), but with the emgd-driver ( [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) ) it worked on 10.10.

now i upgraded to 11.04, so only the standard vesa-driver works anymore with the new x-server
it now sometimes crackles (all sound, even system-sounds. i just mute the netbook for a few minutes and it works again)
sometimes a piece of sound is repeated once (about half a second lasting) and the part which should come is kinda dropped (when listening music, watching videos)

atm i'm trying to downgrade x to 1.9 so emgd works again and i get back 3d acceleration and opengl-support 

Greez

---

