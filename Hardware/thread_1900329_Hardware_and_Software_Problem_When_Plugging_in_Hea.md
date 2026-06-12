---
title: "Hardware and Software Problem When Plugging in Headphones"
date: 2011-12-26
forum: Hardware
---

### Post by weblearner115 on 2011-12-26
Hello everyone,

I'm having a problem with my laptop's audio hardware.  Most of the time, I choose to play audio through my laptop speakers.  But for the first time in a while, I plugged in my headphones.  When I tried to play something, no sound came out of them.  So while I was troubleshooting the problem, I noticed that every time I plug in the headphones, the mute indicator on my laptop transitions from the unmuted color to the muted color.  Ubuntu says that the audio playing on my computer is not muted.  But even though Ubuntu continues to say nothing is muted, I can't help but to think that the hardware is not communicating with Ubuntu correctly.  My laptop is an HP Pavilion dv4-2160us.  Any help would be much appreciated.  Thanks in advance!

weblearner115

---

### Post by weblearner115 on 2012-01-03
Doesn't anybody have suggestions?

---

### Post by MoreOrLess on 2012-01-04
Let's start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by weblearner115 on 2012-01-11
Sorry I didn't answer quicker, MoreOrLess.  I hadn't realized anybody had replied.  I ran the script you sent and here are the results:

[http://www.alsa-project.org/db/?f=d792f1086259fb397579826267d0c10cbca3f953](http://www.alsa-project.org/db/?f=d792f1086259fb397579826267d0c10cbca3f953)

And thanks for helping!  I hope the above information helps. :)

---

### Post by MoreOrLess on 2012-01-11
Try adding this line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=hp
```Then, reload alsa and try the headphone jack again.
```
sudo alsa force-reload
```

---

### Post by weblearner115 on 2012-01-11
I did what you listed, but nothing changed as to how my laptop behaves when my headphones are plugged in.  Any other ideas?

---

### Post by weblearner115 on 2012-02-04
Still having this problem!  Any help would be must appreciated!

---

### Post by xyzzyman on 2012-02-04
open a terminal run alsamixer. See if anything changes when you plug in headphones. Your card may have another volume control channel for your headphones.

---

