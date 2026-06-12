---
title: "What could be the possible solutions?"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by StrikeRTM on 2005-04-06
I hear a pop when doing something, but when trying to play mp3 or watch video using say videolan, then there is simply no sound.

I'm using Gnome and the motherboard with built in sound is this one:
[http://www.abit-usa.com/products/mb/products.php?categories=1&model=79](http://www.abit-usa.com/products/mb/products.php?categories=1&model=79)

---

### Post by bored2k on 2005-04-06
[QUOTE=StrikeRTM]I hear a pop when doing something, but when trying to play mp3 or watch video using say videolan, then there is simply no sound.

I'm using Gnome and the motherboard with built in sound is this one:
[http://www.abit-usa.com/products/mb/products.php?categories=1&model=79](http://www.abit-usa.com/products/mb/products.php?categories=1&model=79)[/QUOTE]
 sudo apt-get install vlc-esd, then go to vlc settings [advanced] and select esound/esd as a sound srvr.

also sudo apt-get install libmikmod beep-media-player, go to preferences and select esound. 

[http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/)

---

### Post by wmcbrine on 2005-04-07
Or, disable esd, and set everything to use alsa. IMHO this will probably get more things working, but YMMV.

---

