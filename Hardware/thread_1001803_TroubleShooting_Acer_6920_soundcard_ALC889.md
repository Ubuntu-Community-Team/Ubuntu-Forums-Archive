---
title: "TroubleShooting Acer 6920 soundcard ALC889"
date: 2008-12-04
forum: Hardware
---

### Post by CJay554 on 2008-12-04
Ok so i wasn't able get sound working out of the box with 8.10 but i have heard that ubuntu uses an older version of ALSA (dont know why)
so i installed headers and installed the newer version of the driver from the ubuntu help:  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
installed it exactly copy/paste
i added my model as acer when editing alsa-base

I went into the volume control preferences from the panel picked "HDA Intel (Alsa mixer) and went down the list and unmuted pretty much all selections (PCM, Front, Front mic, etc)

When i go to sound and test through autodetect nothing, but if i change it to ALSA - Advanced Linux Sound Architecture i CAN hear the long beep sound. The sound though is only present with headphones...

So my card and my driver are working ok... through the beep only.
If i try to play a video on lets say youtube or music through rhythmbox i do not hear anything. But if i do try the beep simulatniously with the music/video the beep gets choppy (theres aconflict when multiple sounds are played)  

The beeping also doesn't sound if i do not have the volume up to 100% if i keep the beep on and go to 99% it cuts in half, then another point and you cant really hear it..

also the beep is inconsistent, when i test it multiple times, sometimes it starts really low and builds up, sometimes it start loud and stays on track.

So its there... but i have no idea where to go from here...

Help would be completely appreciated so we can close this problem once and for all! :popcorn:

---

### Post by binbash on 2008-12-04
I solved the problem here : 

[http://ubuntuforums.org/showthread.php?t=984081](http://ubuntuforums.org/showthread.php?t=984081)

read all thread.

---

### Post by CJay554 on 2008-12-04
Nevermind i fixed it.
on
sudo nano /etc/modprobe.d/alsa-base the "options snd-hda-intel model=MODEL"
you had to add, for Model instead of acer i put in "auto" and i restarted and it detected my sound fine! its pretty good too, not as bad as OSS4 (low volume)

---

