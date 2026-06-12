---
title: "Need help with audio configuration"
date: 2010-04-05
forum: Hardware
---

### Post by L815 on 2010-04-05
I recently bought an Asus u50f laptop. Everything is working great; just need some help configuring the audio drivers. 

The issue is that sound plays out of both the speakers and the headphones when headphones are plugged it. i.e the speakers don't mute themselves.

I've tried a few configurations from some googling but nothing seems to have worked. 

I'll have the laptop in about an hour or so. If there is anything needed for information, let me know and I'll post it up.

Thanks for the help in adv.

Modes I've tried:
```
options snd-hda-intel model=asus
```
```
options snd-hda-intel model=asus-laptop
```
```
options snd-hda-intel model=asus position_fix=1
```
```
options snd-hda-intel model=auto
```
```
options snd-hda-intel model=3stack
```

---

### Post by betes on 2010-05-18
I can't offer a solution, but I wanted to bump this since I have the same laptop and the same problem.  Have you found any solution?

---

### Post by theozzlives on 2010-05-18
It may be how the hardware is wired, have you consulted the documentation?

---

