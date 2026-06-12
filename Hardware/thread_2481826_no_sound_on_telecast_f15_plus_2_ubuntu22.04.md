---
title: "no sound on telecast f15 plus 2 ubuntu22.04"
date: 2022-12-10
forum: Hardware
---

### Post by moralagent on 2022-12-10
new install of ubuntu22.04 on this machine with no sound. 
here is the output
[http://alsa-project.org/db/?f=02a87cb44323438713ff11a8756f0b405cbe6103](http://alsa-project.org/db/?f=02a87cb44323438713ff11a8756f0b405cbe6103)
any help very welcome

 lspci -v | grep -A6 Audio
00:0e.0 Multimedia audio controller: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 06)
	DeviceName: Onboard - Sound
	Subsystem: Device 2782:0306
	Flags: bus master, fast devsel, latency 0, IRQ 129
	Memory at a1210000 (64-bit, non-prefetchable) [size=16K]
	Memory at a1000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

