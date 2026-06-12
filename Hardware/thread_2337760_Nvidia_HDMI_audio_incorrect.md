---
title: "Nvidia HDMI audio incorrect"
date: 2016-09-21
forum: Hardware
---

### Post by timonoj on 2016-09-21
Hi guys,

I have a brand new PC with a brand new Kubuntu 16.04.1 install. The PC has an nvidia 1070 GPU with 3 DP and 1HDMI. I do actually need two HDMIs, so I'm using an adapter in one of the ports. My setup is:
HDMI port: Direct to HDMI monitor. Monitor has speakers/headphones plug.
DP Port: Adapter to HDMI, then HDMI cable to Pioneer amplifier. Amplifier then outputs video to an HDMI TV in the same room, after playing the audio from the HDMI signal.

This setup has been working on a different laptop with no problem for a rather long time, so the amplifier/tv have no issues. Also with Windows 10 on the affected PC, this works flawlessly. 

However, in Kubuntu: There's no way to get the audio to the amplifier. 
[quote]
~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[quote]
After a bit of finicking, I realized no matter what, the audio is going to the headphone jack in the monitor. If I change the output profile for any of the HDMI options available (HDMI, HDMI 2, 3 and 4, each one with subsets for Stereo, 5.1, 7.1 etc)...it doesn't matter. It always sounds from the headphones.

I'm using nvidia drivers nvidia-370. Any ideas guys?

---

