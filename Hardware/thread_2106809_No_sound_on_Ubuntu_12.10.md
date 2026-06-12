---
title: "No sound on Ubuntu 12.10"
date: 2013-01-20
forum: Hardware
---

### Post by Limpaa on 2013-01-20
Hi all,

After upgrading from 12.04 to 12.10 I'm unable to play any audio on my laptop. If I check the audio settings I noticed the sound card is missing on the output/input.

Also in some topics it's discussed to check the alsamixer.

Terminal: aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

Specs: Laptop ASUS K55VD.

---

