---
title: "Sound card (and even sound) detected, but I hear nothing."
date: 2014-07-19
forum: Hardware
---

### Post by atettenb on 2014-07-19
I'm a fairly new Ubuntu user running 12.04 on a Toshiba Satellite S50D laptop.  Since I installed Precise I haven't been able to get sound to come out of the speakers or anything plugged into the headphone jack.  The only thing which works is my usb headset.  

I've run alsa-mixer and pavucontrol and nothing seems to be muted, it seems to have detected the sound card just fine.

The strange thing is when I run pavucontrol and play something with sound, it tells me that sound is coming out of the onboard speakers (or my earbuds if they're plugged in).  I don't hear a thing.

Thanks for any suggestions

---

### Post by Yellow Pasque on 2014-07-19
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by atettenb on 2014-07-19
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=636c2b8a1d91ff584485264ca55acde88c3b775b](http://www.alsa-project.org/db/?f=636c2b8a1d91ff584485264ca55acde88c3b775b)

---

### Post by Yellow Pasque on 2014-07-19
Have another look at alsamixer. It looks like all of the outputs are turned off:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off][
```

---

### Post by atettenb on 2014-07-20
[http://www.alsa-project.org/db/?f=7de8defbba4b07468bcaec65d91f05e7d1619f22](http://www.alsa-project.org/db/?f=7de8defbba4b07468bcaec65d91f05e7d1619f22)

still no sound

---

### Post by Yellow Pasque on 2014-07-20
Did you add this option?
```
snd-hda-intel: model=generic
```

I would remove it. [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by atettenb on 2014-07-20
Alright, I did that.  I also tried the hda jack retask tool mentioned in that article.  All to no avail.

---

### Post by Yellow Pasque on 2014-07-20
:\
If it was me, I would try a LiveUSB of the latest Ubuntu: [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)
Since you're running an old version, it's always good to make sure it hasn't been fixed already before you file a bug report or try to modify your current install.

---

