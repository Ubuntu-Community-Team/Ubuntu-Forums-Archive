---
title: "Sound Popping In 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by jrb470 on 2009-11-06
Hi All!

I have that dreaded sound popping issue and I tried to comment out the last line in /etc/modprobe.d/alsa-base.conf but it isn't accepting it.

I added a # to the beginning of the last line but it wont let me save it.

Im a bit new to Ubuntu and Im not sure what to do!

Thanks!!!

---

### Post by wojox on 2009-11-06
Try:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

You need root permissions.

---

### Post by jrb470 on 2009-11-06
Thank you so much!!!

It worked!!

---

