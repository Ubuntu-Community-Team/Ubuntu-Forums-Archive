---
title: "Sound Problems With DV6000"
date: 2010-06-09
forum: Hardware
---

### Post by linux.is.skynet on 2010-06-09
Installed Lucid on my laptop and the sound only works through the headphone jacks. The webcam and mics work, just not the speakers.  Here's the output of aplay -l :

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Tried the backport module of alsa like another thread recommended, but it didn't help. Help? I DO NOT want to run XP! lol

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by linux.is.skynet on 2010-06-09
The laptop is a HP DV6439NR of the DV6000 series. Just installed the wifi by installing the b43-fwcutter package. 

Here's my terminal output:


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
justin@AMD-MEDIA:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
justin@AMD-MEDIA:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20549 (Venice)

---

### Post by lidex on 2010-06-09
I would suggest removing alsa-backports, rebooting, and then follow the alsa-upgrade link in my sig to get v 1.0.23

---

