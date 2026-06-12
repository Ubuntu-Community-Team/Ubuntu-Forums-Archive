---
title: "Microphone input sounds awful"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Radonballoon on 2007-06-01
I have an ati ac97 soundcard on a gateway laptop, and i was trying to record via the mic input in audacity, and it sounds awful. It sounds distorted with a shrill pitch behind it. Does anyone have any ideas as to how to fix this?

---

### Post by Zackie on 2008-01-17
yeah i'm having a problem with this as well... Min Is just rough and Grainy sounding with distorted clicks... Windows with Cakewalk/Adobe Audition... this wasn't an issue... any ideas?

---

### Post by eggdeng on 2008-01-17
The following has been helpful to some of us with microphone problems.
Back up your esd.conf 
```
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf.bkup
```
Open the original file
```
sudo gedit /etc/esound/esd.conf
```
& replace everything with the lines
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
Rename your asound.conf if it exists
```
sudo mv /etc/asound.conf /etc/asound.conf.bkup
```
Again you will be able to revert if things don't work out.
Reboot for changes to take effect.

---

