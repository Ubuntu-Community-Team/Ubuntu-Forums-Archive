---
title: "running ubuntu 11.10 on an LG C1, recognises sound card, but no audio!!?!?"
date: 2011-12-11
forum: Hardware
---

### Post by madad123 on 2011-12-11
hey guys, I just installed ubuntu on my LG C1 netbook and i cant figure out why the audio isnt working, when I type aplay -1 into the terminal I get this list of hardware devices.

  aplay -l
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Anyone got any ideas? I'm new to linux and im still trying to   figure it out. Enjoying it so far regardless of audio problems,
anyway please reply cheers!

---

### Post by madad123 on 2011-12-11
**Also** : cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: LSI Si3054

 lspci -nn | grep -i audio 
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)

---

### Post by robn30 on 2011-12-28
Did you ever get this fixed?  I am having the same issue with my Asus P5NE-SLI MB.  I can't figure out how to get the damn sound to work.  It is really pissing me off.  I have spent all day trying to figure this out.

---

