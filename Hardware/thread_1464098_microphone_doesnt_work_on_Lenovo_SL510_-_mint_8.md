---
title: "microphone doesnt work on Lenovo SL510 - mint 8"
date: 2010-04-27
forum: Hardware
---

### Post by chargingrhino on 2010-04-27
i have a Lenovo SL510 with mint 8 on it. After I installed it, microphone and webcam worked good on skype.  I installed some updates, no level 3 updates, and saw that my mic didnt work on skype. I checked all sound options through pulseaudio, everything is how it should. Checked alsamixer, have everything unmuted and all volumes up like it should be. when i use sound recorder, records no audio, just static playback. when i adjust mic levels in alsamixer, the higher the level the louder the static i hear from speakers. its wierd. in my sound preferences-input, input level meter ranges from 3 to 4 to 6 lines, so i know its there.  if anyone knows what i can do and can explain it to me pretty good that would be awesome. 
is there way is to get a list of all the updates that were installed when i did update, because then i could uninstall them one by one till i get the one that messed up my mic. if this will work and someone knows how to do this and can help me out that would be awesome. i dont want to have to uninstall and reinstall mint again!theres got to be a way to fix it some how.  thanks in advance
:guitar:

---

### Post by lidex on 2010-04-27
Had you previously done an alsa upgrade? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

