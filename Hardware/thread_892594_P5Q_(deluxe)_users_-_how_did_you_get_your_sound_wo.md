---
title: "P5Q (deluxe) users - how did you get your sound working?"
date: 2008-08-17
forum: Hardware
---

### Post by Doctoxic on 2008-08-17
Hi

I have a new build of 8.04 on an Asus P5Q deluxe mobo but i don't have any sound

does this info help?


aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices ID 989b

If you have this mobo did sound work for you with no probs 'out of the box'?

thanks

Diss

---

### Post by ferrari355f1 on 2009-04-22
I am also having the same problem. If anyone has a solution that would be great. I'll be sure to post it here if I come across a solution.

---

### Post by rmac75 on 2009-05-13
if you type
```
lspci -v
```
and get a bunch of stuff back to include:
```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8311
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: **snd-hda-intel**
```

You need to load the kernel module for the controller
sudo nano /etc/modules
add "snd-hda-intel" at the end of the file.

Also, I did have an issue with the headphones not working until I enabled PCM within the sound panel (click on the speaker icon in the upper right hand panel, and select volume control and play with PCM-2.

You can also try alsamixer from the command line, that is how I saw that the headphone jack was off.

Reboot to load the module. Hopefully this will do the trick for you.

---

