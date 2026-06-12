---
title: "ALC989 Drivers Not working"
date: 2013-10-23
forum: Hardware
---

### Post by Danny_Michel on 2013-10-23
I tried downloading these drivers and installing them for my motherboard. it worked, but my rear left and rear right speakers arent working. Also, my USB headphones arent working either [https://bbs.archlinux.org/viewtopic.php?pid=1203138#p1203138](https://bbs.archlinux.org/viewtopic.php?pid=1203138#p1203138)

> danny@danny ~ $ lspci | grep Audio00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
danny@danny ~ $  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




---

