---
title: "HDMI audio stopped working when kernel 3.19.0-18 installed"
date: 2015-05-28
forum: Hardware
---

### Post by dennis-furr on 2015-05-28
HP Split X2 running Vivid Vervet (upgraded from Utopic Unicorn) was working fine with audio via HDMI until I installed updates that included a new kernel.  Audio is OK through the laptop speakers and with a USB headset.  

*aplay -l*
**** List of PLAYBACK Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: 92HD95 Analog [92HD95 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I managed to break PulseAudio and ALSA, possibly caused by me migrating my home folder to a different drive or my recent playing with i3wm but I have ALSA working again.  PulseAudio isn't fixed yet but I'm working on it.  No less, I'd expect to see a HDMI entry out of aplay.

This is starting to get a bit out of my comfort zone so any advice would be welcome.

---

