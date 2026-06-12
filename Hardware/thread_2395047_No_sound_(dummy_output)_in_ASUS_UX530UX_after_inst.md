---
title: "No sound (dummy output) in ASUS UX530UX after installing nvidia drivers and cuda 9.2"
date: 2018-06-26
forum: Hardware
---

### Post by miguel-carcamo on 2018-06-26
I have bought a Zenbook ASUS UX530UX, and I have installed Ubuntu 16.04.1

Before installing NVIDIA drivers, sound worked like a charm, I could turn the volume up and down without problems.

Nevertheless, when I installed the NVIDIA drivers through the CUDA Toolkit 9.2, the sound went off and when I went to sound properties the only device was a dummy output. The sound is back only if I turn off and then turn on the notebook, but in this case, the volume does not change as I turn the volume up or down, in other words, it remains static. Additionally, sometimes when the sound is back, only the left speaker of the notebook sounds.

The output of aplay -l, when the sound "works" is:
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Please I would be very delighted to hear help from someone with similar issues.

---

