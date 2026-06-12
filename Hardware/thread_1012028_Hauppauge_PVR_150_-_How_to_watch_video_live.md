---
title: "Hauppauge PVR 150 - How to watch video live?"
date: 2008-12-15
forum: Hardware
---

### Post by SupaRice on 2008-12-15
I'm running Hardy...

So I've got a Hauppauge PVR-150 card, (retail not MMC).  My machine recognizes the card, but program do I use to watch live video from it?  I'm trying to watch my security camera via the RCA Video input on the card.  

I've searched and most everything I've found is in regards to recording TV.

```

# dmesg | grep Hauppauge
[   38.704892] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   38.790265] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial#
[   38.790277] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   39.200394] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150

```

---

### Post by SupaRice on 2008-12-15
OK, so I've happened across this:

[http://ubuntuforums.org/showthread.php?t=655523&highlight=hauppauge+rca+video](http://ubuntuforums.org/showthread.php?t=655523&highlight=hauppauge+rca+video)

Which shows to do this:

```
v4l2-ctl -i 2
```

So now I get a picture, but it's massively distorted.  How do I "tune" it to get the picture to be right?

[IMG]http://i6.photobucket.com/albums/y213/suparice/ea5ae288.png[/IMG]

---

