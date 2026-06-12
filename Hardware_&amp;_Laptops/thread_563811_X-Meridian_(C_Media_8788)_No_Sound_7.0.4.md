---
title: "X-Meridian (C Media 8788) No Sound 7.0.4"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by Deckard79 on 2007-09-30
Hi folks!

This is my first post here, and I am a new convert to Linux and Ubuntu, so please forgive the ignorance... ;)

Installed 7.0.4 just fine, but unfortunately my Auzentech X-Meridian (based on C-Media 8788) shows no signs of life.

Sound Prefs Test simply displays 

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

I tried upgrading ALSA to version 1.0.15 - did ./configure, make, make install and ./snddevices - this process seemed to work.  Sadly though, it has had no effect whatsoever - still no sound and still the same "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing" error!

This is driving me nuts - I love the look of Ubuntu so far, but if I can't get sound working... what's the point? :(

---

### Post by Deckard79 on 2007-10-01
*Bump*

Anyone...?

---

### Post by geraldm on 2007-10-01
CMI8788 chip is unsupported.  see 
[www.alsa-project.org/main/index.php/User:ClemensLadisch](www.alsa-project.org/main/index.php/User:ClemensLadisch)

Gerald

---

### Post by elliio on 2007-10-24
Hi all,

I have an X-Meridian, and if anyone knows who to contact on the ALSA team driver developer(s) working on this, please contact me.

Since I can't use the card, I can test out driver betas, or temporarily donate it to the driver developers so that the darn driver can be written.

About me: I'm an audiophile, and this is an excellent audiophile quality board (custom circuit design, upgradeable Operational-Amplifiers, up to 120db in Windows XP x64, Windows Vista Ultimate x86, etc). Though the point here is to get drivers written and working and packaged for Ubuntu.

-elliio

---

### Post by Anaximander Thales on 2007-11-13
Don't know if you've seen this topic yet --
[New Alsa Testing -- CMedia 8788 chipset -- need help](http://ubuntuforums.org/showthread.php?t=527341&highlight=CMI8788)

I've been trying to keep people aware of what's going on.  As of right now, CLadisch has gotten a card is busy re-writing the cmedia driver for the CMI8788 chipset.

Right now -- if you want sound -- you can use the OSS driver.  That does work for the most part.

---

