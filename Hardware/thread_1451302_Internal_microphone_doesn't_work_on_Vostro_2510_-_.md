---
title: "Internal microphone doesn't work on Vostro 2510 - intelhda ALC268"
date: 2010-04-10
forum: Hardware
---

### Post by AKM144204 on 2010-04-10
Testing with an updated Lucid 10.04 Beta, the internal microphone doesn't work for Sound Recorder. I can play music and video sound but not recording with my own voice.  After append the following line to /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=auto.Then reboot.
I am getting "No sound".

$ uname -r
2.6.32-19-generic

$ cat /proc/asound/card*/codec\#*|grep -i codec
Codec: Realtek ALC268

My ALSA info script is located at
[http://www.alsa-project.org/db/?f=0163a886d9c4f48f6f504ae015629abeed4a50bc](http://www.alsa-project.org/db/?f=0163a886d9c4f48f6f504ae015629abeed4a50bc)


Also please attached screenshot for
- Sound Preferences
- Multimedia Systems Selector
- ALSAMIXER
- alsa-base.conf script file


Please advise how can I solve this?

---

### Post by lidex on 2010-04-11
Try going to "System>Preferences>Sound" and play around with the settings on the "Input" tab.

---

### Post by lidex on 2010-04-11
I'm sure you realized to remove that entry:
```
options snd-hda-intel model=auto
```
A better one would be:
```
options snd-hda-intel model=dell
```

---

