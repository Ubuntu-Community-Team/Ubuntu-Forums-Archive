---
title: "[Audio] Sony external mic non recognized on Karmic"
date: 2010-04-26
forum: Hardware
---

### Post by DardDiablo on 2010-04-26
Hi over there guys,

My friends recently give me as a gift a Sony ECM-CS10 external mic (not usb but with the standard jack connection) but there's no way to use it :(. The system simply doesn't recognized it and shows me only the internal mic.

My computer is a Samsung NC10, and I have the 2.6.31-20 kernel installed (but also with the previous versions the mic isn't working).

I've searched everyday the past week but nothing helped me (I tried also to remove and reinstall pulseaudio).I've tried installing:

linux-backports-modules-2.6.31-20-generic
linux-backports-modules-alsa-2.6.31-20-generic

```
aleppe@aleppe-pc:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC272
```

I attach you some images to explain better my problem (the system is in italian I hope it doesn't matter):

[[IMG]http://img541.imageshack.us/img541/9041/audio1.th.png[/img]](http://img541.imageshack.us/i/audio1.png/) [[IMG]http://img406.imageshack.us/img406/114/audio2.th.png[/img]](http://img406.imageshack.us/i/audio2.png/) [[IMG]http://img406.imageshack.us/img406/1944/audio3.th.png[/img]](http://img406.imageshack.us/i/audio3.png/)

I hope that someone could help me otherwise I have to change this mic with a new one. Thanks in advice and sorry for my english :P

---

