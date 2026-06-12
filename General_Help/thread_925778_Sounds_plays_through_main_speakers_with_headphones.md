---
title: "Sounds plays through main speakers with headphones plugged in?"
date: 2008-09-21
forum: General Help
---

### Post by Repentless on 2008-09-21
On Windows, when I plug my headphones into the jack in my laptop, the sound stops coming through the laptop speakers and plays only through my headphones.

On Ubuntu, when I plug my headphones in, the sound plays through both the speakers AND the headphones.

Any way to fix this? It's annoying, and help would me GREATLY appreciated. :KS

Oh, I just found a temporary solution: Opening up the volume control and muting the front speakers.

However, it would be nice if it happened automatically. Any way to fix this?

---

### Post by eggdeng on 2008-09-21
Post the output of ```
aplay -l
``` & the make and model of your box.

---

### Post by tjlane on 2008-09-21
I have the same problem- 

> josh@josh-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


On a Toshiba Satellite A305D.

---

### Post by eggdeng on 2008-09-21
It's usually necessary to edit the relevant config file to solve routing problems with Intel HDA cards. Open the file
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add the line
```
options snd-hda-intel model=toshiba
```
to the bottom of the file, save and reboot. This is a first try & may or may not work. Other options you might try are
```
options snd-hda-intel model=auto
```
or
```
options snd-hda-intel model=3stack
```
Remember to [COLOR="Red"]reboot[/COLOR] for changes to take effect.

---

### Post by tjlane on 2008-09-21
That worked perfectly! Thank you very much!!

---

### Post by drdivad on 2008-09-26
same issue, sound coming out of both speakers and the line in (headphones/external speakers)...

I have an Acer Aspire One netbook and have looked on various dedicated Acer Aspire One forums with nothing... added options snd-hda-intel model=acer to the bottom of the alsa-base but still nothing... also downloaded Kmix and while playing around wasn't able to solve the issues... 

help anyone :)

---

### Post by drdivad on 2008-09-27
nobody knows a fix? I'd imagine it's a relatively common issue (many people with different laptops have the same problem)... help is really appreciated.

---

### Post by drdivad on 2008-10-07
no one?

---

