---
title: "HP Touchsmart 9300 Internal Mic Doesn't Work"
date: 2011-08-18
forum: Hardware
---

### Post by UAConspiracy on 2011-08-18
Hi, I've recently been trying to get the HP Touchsmart 9300 Elite running Ubuntu. Dual touch works, sound works, webcam works, nvidia gfx card works (not sure actually, seem like they do, and I don't have bumblebee). But my problem is with the internal microphone. I am not able to capture any input from it.

uname -a
```
Linux Touchsmart 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```alsactl -v
```
alsactl version 1.0.22
```However, I have 1.0.24 snd-hda-intel drivers installed in /lib/modules/`uname -r`/updates/

lspci -nn | grep Audio
```

00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0bea] (rev a1)
```lsusb
```
Bus 002 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 003: ID 0461:4d0f Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0408:3008 Quanta Computer, Inc. 
Bus 001 Device 003: ID 04f2:b2a4 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
cat /proc/asound/card0/codec#0 | grep Codec
```
Codec: IDT 92HD89D3
```
cat /etc/modprobe.d/alsa-base.conf | grep snd-hda-intel
```
options snd-hda-intel enable_msi=1
```
The models I tried so far are: ref, hp, auto.
ref gave me an extra capture channel in alsa, and also another Internal Mic called "Internal Mic 1" But, no luck. Reverted back to no model being specified.

Alsa debug script output: [http://www.alsa-project.org/db/?f=e1cbe7c3470a058216383d3328103df93b2c3c28](http://www.alsa-project.org/db/?f=e1cbe7c3470a058216383d3328103df93b2c3c28)

I'm also having no luck with an external mic in jack working, but I haven't tested it well enough.

Thank you

---

### Post by UAConspiracy on 2011-08-18
Sorry for the double post, but I managed to get model=ref working with sound and an external mic from the mic in jack. 

arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

Still no internal mic though :(

---

