---
title: "Static sound (HP EliteBook 8540p, Ubuntu 11.04 (Natty))"
date: 2011-08-05
forum: Hardware
---

### Post by Nahbyr on 2011-08-05
Hi,

I recently got an HP EliteBook 8540p from work and installed Ubuntu on it. When I plug in my headphone I can hear the music, but it's got a lot of static. I have not yet tried sound through the laptop's speakers (can't start playing music at work, so it'll have to wait until later today if you want me to test that).

Is there someone who can help me fix this? Mind you, this is the first time ever for me to use Ubuntu.

Some stuff I've already tried:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
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

And:

$ lspci -v
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 1521
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

If I need to post more information then just ask and I'll post it asap.

Thx,

---

