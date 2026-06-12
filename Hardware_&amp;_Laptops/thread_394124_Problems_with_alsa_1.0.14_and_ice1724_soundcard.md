---
title: "Problems with alsa 1.0.14 and ice1724 soundcard"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by miceagol on 2007-03-26
I just installed the newest version of Alsa (1.0.14rc3) to get full support for my soundcard with an ice1724 chip. Installation went fine, but when I run
```

sudo modprobe snd-ice1724

```
it just hangs there doing nothing. This also happened when I tried alsa version 1.0.13. My soundcard is listed as UNCLAIMED in lshw.

---

### Post by miceagol on 2007-04-06
This was probably caused by forgetting
```

/etc/init.d/alsa-utils stop

```
before installing

---

