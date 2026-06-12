---
title: "sound not wokring"
date: 2009-09-18
forum: Hardware
---

### Post by anuragupadhaya on 2009-09-18
i have installed ubuntu 9.04
the first thing i want to mention is that i am newbie to linux....i know much deeper in windows than in linux...

After installing ubuntu i can see all the controls for sound....but when i am testing the sound ...i can't hear anything...i have tested the sound levels too but still not working...

any solutions?

---

### Post by Zoot7 on 2009-09-18
Can you post the output of 
```
aplay -l 
```
and 
```
lspci | grep audio
```

Also have you tried using the Gnome Alsa-Mixer? Often no sound is just a case of unmuting an option, and low volume just a case of maxing out the sliders in that.
```
sudo apt-get install gnome-alsamixer
```

---

### Post by anuragupadhaya on 2009-09-18
result for ```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


and result for ```
lspci | grep audio
``` was nothing...just nothing

anf for gnome-alsamixer ....i installed and checked and unmuted everything and i maxed all levels....but still no success

---

### Post by Zoot7 on 2009-09-18
Curious, ALSA recognizes your audio device it seems. 
Is it selected in the Volume Preferences? And is it only one application or all applications?

One possible solution might be to upgrade ALSA to the latest version, have a look at this thread:
**[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")**
Normally I wouldn't recommend upgrading ALSA if you're new to Linux, but that script that's posted there makes it extremely easy.

---

### Post by anuragupadhaya on 2009-09-21
thanks very much for referring to that post..
i successfully upgraded the alsamixer....and sound is working now...

---

