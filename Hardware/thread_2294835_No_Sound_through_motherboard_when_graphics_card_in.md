---
title: "No Sound through motherboard when graphics card installed"
date: 2015-09-13
forum: Hardware
---

### Post by techn0scho0lbus on 2015-09-13
When I have a graphics card installed I do not have any sound from my computer's audio jacks. 

KDE Mixer lists only one playback device: "GM 204 (my video card) High definition audio controller HDMI"

alsamixer will not run in command line 

"aplay -l" doesn't show the motherboard sound, but when i don't have the graphics card installed it does show the motherboard sound and lists it as 'card 0':

**** List of PLAYBACK Hardware Devices ****
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





I've already tried crating a /etc/asound.conf 

pcm.!default {
type plug slave.pcm {
type hw card 0 device 0
}
}
but no luck. 



Anyone have suggestions?

---

### Post by Yellow Pasque on 2015-09-13
If you've got a Skylake CPU/mobo, and Ubuntu 15.04, you need to update the sound module:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

> I've already tried creating a /etc/asound.conf

Delete it.

---

