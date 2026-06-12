---
title: "realtek HD audio is detected, pavucontrol says it works, but i get no sound"
date: 2014-11-12
forum: Hardware
---

### Post by rms2 on 2014-11-12
ive got a problem with realtek HD audio on my system, it appears to work fine, but i get no sound out of the jack on my motherboard. my system has a dedicated sound card which i use for the front panel jacks, and to save myself from having to put up with realteks drivers on windows, and while it does me just fine for most things, id like to use the onboard audio to drive a set of speakers. the front panel jack cant be used because for some reason its significantly quieter than the jacks at the back.

heres a list of detected sound devices from aplay -l
> 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DGX [Xonar DGX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DGX [Xonar DGX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: HDMI_1 [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


heres an image of pavucontrol set to output to the onboard audio
[ATTACH=CONFIG]257911[/ATTACH]

---

### Post by rms2 on 2014-11-12
probably worth mentioning ive already tried the suggestions in [http://ubuntuforums.org/showthread.php?t=1723051](http://ubuntuforums.org/showthread.php?t=1723051) to no avail

---

