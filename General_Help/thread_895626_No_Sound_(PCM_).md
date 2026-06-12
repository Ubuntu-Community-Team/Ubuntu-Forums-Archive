---
title: "No Sound (PCM ?)"
date: 2008-08-20
forum: General Help
---

### Post by TyVadale on 2008-08-20
I am new to Ubuntu/Linux. I installed Ubuntu Hardy and cannot get any sound. I have the M-Audio Delta 1010lt(ice1712) sound card. I can go to system-> Prefernce-> Sound and test the sound from there and get the test to work. I have all options set to the ALSA driver. However I get no system sound. I also cannot get sound to route from JACK to my speakers. In JACK, under connection I don't have the ALSA_PCM connections. Instead I have SYSTEM and under it i have Playback_1 thru Playback_10. I also have Rosegarden installed. When I play a file in Rosegarden I can get it to play back thru my MIDI keyboard but not my main speakers.Do I need to install ALSA_Plugin? Any direction on this will be greatly appreciated.

---

### Post by qstraza on 2008-08-20
try running alsamixer from terminal and check if u have MM on master or front.

---

### Post by TyVadale on 2008-08-21
I Have MM on Master

---

### Post by qstraza on 2008-08-21
> **TyVadale said:**
> I Have MM on Master

So press 'M' and it should unmute master than press esc and sound should work ;)

---

### Post by TyVadale on 2008-08-22
It wasn't muted. I have been able to get a CD to play. I also can play a .wav file from the CLI using aply -vv file.wave. But regular system sounds are not working and I cannot get any sound when using JACK. I did uninstall Pulse Audio and install esound and the sounds worked fine. However JACK would not start with esound installed.

---

