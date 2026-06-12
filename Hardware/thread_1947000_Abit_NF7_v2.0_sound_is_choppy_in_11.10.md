---
title: "Abit NF7 v2.0 sound is choppy in 11.10"
date: 2012-03-25
forum: Hardware
---

### Post by chowno on 2012-03-25
Hello, I'm wondering if anyone has seen any threads related to the sound card used on the Abit NF7 v2.0 motherboard.  I just freshly installed Ubuntu 11.10 and the sound is really choppy for some reason.  Also, in prior versions of Ubuntu I was able to use this thread [http://ubuntuforums.org/showthread.php?t=1608804&highlight=iec958]("http://ubuntuforums.org/showthread.php?t=1608804&highlight=iec958") to allow Dolby 5.1 surround though the optical audio out on the motherboard but it seems that the Alsa stuff has gotten moved around a bit - I need to know where Alsa is keeping its drivers now or a possible alternative fix but this is low priority as I would like to have sound that isn't choppy.  Here is my aplay -l output...  Thanks for any advice!

```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by chowno on 2012-03-25
Okay I tested my optical connection and it is not choppy, only the analog connection seems to be affected.

---

