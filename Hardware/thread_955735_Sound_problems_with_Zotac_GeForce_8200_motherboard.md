---
title: "Sound problems with Zotac GeForce 8200 motherboard"
date: 2008-10-22
forum: Hardware
---

### Post by iseletsk on 2008-10-22
I have crackling sound with Zotac GeForce 8200 motherboard & Ubuntu 8.04.
It has built in sound card which gets detected as:
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The module that gets loaded is snd_hda_intel, but the sound is cracking and/or sometimes choppy.
Does anyone know if there is a better driver for this card, or is it not supported yet?

Thanks,
Igor.

---

### Post by Lord Xeb on 2008-10-22
use alsa-base 

```
sudo apt-get install alsa-base
```

---

### Post by teaker1s on 2008-10-22
try looking [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by iseletsk on 2008-10-22
Thanks a lot.
Same problem after re-compiling to  alsactl version 1.0.18rc3
Trying to find right options didn't help as well :(

---

