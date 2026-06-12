---
title: "Ubuntu on Dell 1735  mike and speaker issue."
date: 2009-01-14
forum: Hardware
---

### Post by rajeshckk on 2009-01-14
I have just got the dell 1735 laptop and installed ubuntu 8.10 and I have issues with the logitech mike and the inbuilt mike recording sounds.
I can listen the echo sound using the speakers, so the speakers do work, but this is also laptop speakers work but not the usb speakers.

rajesh@rajesh-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rajesh@rajesh-laptop:~/ alsactl -v
alsactl version 1.0.17
rajesh@rajesh-laptop:~$ 

I am not sure what other things to check in this to get the mike working. But this has become a major issue.

I can try to check if there are any hints to check.

---

