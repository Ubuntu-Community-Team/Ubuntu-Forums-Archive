---
title: "Sound issues...."
date: 2010-06-23
forum: Hardware
---

### Post by Stobei117 on 2010-06-23
Heya All,

I have a Area 51 M15x laptop, i was running 32 10.4 ubuntu till about a week ago when i put 64 bit on it, and when i did, the speakers dont work for the laptop, when i plug in headphones they do work, i had the same problem with the 32 bit, and one day they started to work, is there a way to make ubuntu scan for hardware? see if it can start the speakers again. or is there a fix for this?

Thanks!

---

### Post by Yellow Pasque on 2010-06-23
From searching web, this is common. The remedy:

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Copy/paste this line to the end of the file:
```
options snd-hda-intel model=lenovo101e
```
If lenovo101e doesn't work, you could also try model=mbp3

---

