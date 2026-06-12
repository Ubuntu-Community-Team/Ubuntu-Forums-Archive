---
title: "HEadphone jack"
date: 2008-06-21
forum: Hardware
---

### Post by jenova_skill on 2008-06-21
Sound works fine I got the sound 2 stop when a headphone is plugged in the jack but no sound comming out.......
Toshiba Satellite  (laptop) 
I tried a few posts guides..... seems something reinstalling a driver specific to that computer is needed. However im ignorant to what i need to put into the shell for this particular thing.

---

### Post by Nepherte on 2008-06-21
Let's figure out what codec you are using:
```
cat /proc/asound/card0/codec#* | grep Codec
```

What laptop (brand) do you have?

---

