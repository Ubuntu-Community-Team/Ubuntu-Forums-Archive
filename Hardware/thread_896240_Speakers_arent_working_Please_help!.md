---
title: "Speakers arent working Please help!"
date: 2008-08-21
forum: Hardware
---

### Post by JECHO on 2008-08-21
Hey guys i just picked up a sony vaio vgn-ar850eand some 2.1 altec lansing speakers... the problem is that when i plug in the speakers (into the headphone jack) the sound isnt being directed out of them. It stays coming out of the built in notebook speakers. im running ubuntu 8.04 any help is appretiated

---

### Post by thehellboy on 2008-08-21
check the working of your speakers with TV or other os.. where they working properly?

---

### Post by JECHO on 2008-08-21
> **thehellboy said:**
> check the working of your speakers with TV or other os.. where they working properly?

yeah... ive got the machine dual booting with vista and they're working there. Im thinking that i just dont have the linux drivers...

---

### Post by thehellboy on 2008-08-21
usually audio drivers will be available by default.. and try updating drivers.. that may help you

---

### Post by JECHO on 2008-08-21
> **thehellboy said:**
> usually audio drivers will be available by default.. and try updating drivers.. that may help you

Yeah the audio driver for the internal speakers was installed by default but no luck with the externals. Ive done all of the updates as well and still no luck :confused:

---

### Post by eggdeng on 2008-08-21
Post the output of
```
aplay -l
```
What make & model is your box?

---

### Post by JECHO on 2008-08-21
> **eggdeng said:**
> Post the output of
```
aplay -l
```
What make & model is your box?

Output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Im on a VGN-AR850E Sony Vaio

---

### Post by eggdeng on 2008-08-21
Try
```
gksudo /etc/modprobe.d/alsa-base
```
Copy and paste the line
```
options snd-hda-intel model=vaio
```
at the bottom of the file. Save and _reboot_.
This may or may not work for you but something of this kind is usually necessary to sort out Intel HDA routing problems. More info at [http://http://ubuntuforums.org/showthread.php?t=314383]("http://http://ubuntuforums.org/showthread.php?t=314383")
If you get no joy with ```
model=vaio
``` you might try ```
model=auto
```

---

### Post by JECHO on 2008-08-22
> **eggdeng said:**
> Try
```
gksudo /etc/modprobe.d/alsa-base
```
Copy and paste the line
```
options snd-hda-intel model=vaio
```
at the bottom of the file. Save and _reboot_.
This may or may not work for you but something of this kind is usually necessary to sort out Intel HDA routing problems. More info at [http://http://ubuntuforums.org/showthread.php?t=314383]("http://http://ubuntuforums.org/showthread.php?t=314383")
If you get no joy with ```
model=vaio
``` you might try ```
model=auto
```


excellent! that worked! :) thanks a lot man

---

