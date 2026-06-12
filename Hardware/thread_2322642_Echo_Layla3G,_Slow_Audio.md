---
title: "Echo Layla3G, Slow Audio"
date: 2016-04-29
forum: Hardware
---

### Post by caustin-s on 2016-04-29
I apologize if this is not the correct forum to post this question, but I needed to go somewhere.

I am running a DAW (Ubuntu 14.04) with an Echo Layla3G soundcard (ALSA driver version k3.13.0-85-generic).  When I run sound through this card the sound is running very slowly (about half speed).  When I run sound through the on-board card, audio runs as expected.

I am very ignorant when it comes to understanding the relationship between hardware/application/jack/pulseaudio/ALSA, etc.  Could this be an issue with the master clock in the echo card?  I have searched online for hours but haven't found any meaningful directions to follow.

Can anyone help point me in the right direction?  Thanks in advance.

Here is a little information to start.  Let me know if more is needed.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Layla3G [Layla3G], device 0: Analog PCM [Layla3G]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Layla3G [Layla3G], device 1: Digital PCM [Layla3G]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by caustin-s on 2016-05-02
Bump.

---

