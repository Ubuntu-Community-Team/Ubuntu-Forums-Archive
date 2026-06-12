---
title: "Problems with sound (Hda Nvidia)"
date: 2009-08-21
forum: Hardware
---

### Post by tsmithtree on 2009-08-21
I'm running Ubuntu 9.04 x86_64 on a Dell Studio 14z with nvidia 180 series graphics driver. Audio did not work until I installed the nvidia graphics driver. Sound works, but I have to turn the volume all the way up before I can hear it and the quality is pretty bad. On windows, the quality was much better and the sound was much louder. I have completely removed pulseaudio (which I hate with a passion), and the problem still persists. Also the built-in mic does not work, but that's not so much an issue as the audio volume.

lspci:
nVidia Corporation MCP79 High Definition Audio (rev b1)

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Could it be a problem with HDMI sound support?

Everything is unmuted and turned up to the maximum in alsamixer. I have switched everything to ALSA in the gnome sound preferences, but I get the same problem regardless of what settings I use there.

---

