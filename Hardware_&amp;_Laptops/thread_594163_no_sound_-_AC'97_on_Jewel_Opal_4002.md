---
title: "no sound - AC'97 on Jewel Opal 4002"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Knoeki on 2007-10-27
I have a Jewel Opal 4002 laptop. nice thinggy, but I'm having sound issues... I get no sound at all, but the sound device *is* recognized. I followed [this guide](http://ubuntuforums.org/showthread.php?t=205449), but no such luck v.v

the drivers available on the Realtek website are all dead links

upon doing **aplay -l** I get:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

any ideas? or do you need more info? hopefully someone can help

(( yes, I did check my volume settings ))

---

### Post by Knoeki on 2007-10-28
Right, I fixed the problem... I discovered a volume wheel, which is easily overlooked >.>

very stupid, I know -_-'

---

