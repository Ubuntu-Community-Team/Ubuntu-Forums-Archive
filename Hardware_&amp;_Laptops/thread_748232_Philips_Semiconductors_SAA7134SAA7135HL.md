---
title: "Philips Semiconductors SAA7134/SAA7135HL"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by kastekm on 2008-04-07
Hello!
Anybody configured this card on Ubuntu?
lspci:
```
00:06.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```

Tvtime:
```
kozik@Kozik:~$ tvtime
Uruchomione tvtime 1.0.2.
Czytanie konfiguracji z /etc/tvtime/tvtime.xml
Czytanie konfiguracji z /home/kozik/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

---

### Post by profediego on 2008-05-23
Hey, i got the same TV Tuner card, and i cant make it work on Ubuntu or any other distro, could someone help here please.

---

### Post by rikdeek on 2008-06-20
Hi there,
  I too have this tuner card, and haven't managed to get it working yet.

There's this:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

But, it looks to be out of date now, and i'm not sure how well all that stuff relates to ubuntu.

Anyone know of a good place to start, a tutorial for installing tv tuners on ubuntu?

If I work it out, I'll be sure to let you know.
Cheers,
   - Rik

---

