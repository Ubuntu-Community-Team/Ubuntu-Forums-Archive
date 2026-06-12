---
title: "[SOLVED] device /dev/dsp busy"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by Megaqwerty on 2007-05-08
I've been getting this error lately: ```
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
``` 
Any idea how to fix it, or its counterpart?
```
 Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy"
```

Thanks,

Megaqwerty

---

### Post by Megaqwerty on 2007-08-10
Sorry for not posting the answer sooner, but I had forgotten I had a thread for this.

Anyway, the solution is to close other programs that may be using the sound device, (such as Firefox) when those are closed, this error will go away.

-Megaqwerty

---

