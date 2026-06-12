---
title: "No sound on my Gateway 4024GZ"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by Nicallen63 on 2007-12-22
Hey everyone i recently installed Ubuntu Studio on my Gateway 4024GZ and i have no sound. When i go to Sound Preferences it shows the following items for sound playback:
Autodetect
Intel 82801DB-ICH4 Modem-Modem
Intel 82801DB-ICH4 - IEC958
Intel 82801DB-ICH4 - ICH4
ALSA
ESD
OSS

The computer will play songs but will not produce any sound. I have never had a message telling me that there is no sound card installed, and i havent been able to find any Linux drivers for the sound card. Anyway help or suggestions would be appreciated.

---

### Post by TheLions on 2007-12-22
> **Nicallen63 said:**
> Hey everyone i recently installed Ubuntu Studio on my Gateway 4024GZ and i have no sound. When i go to Sound Preferences it shows the following items for sound playback:
Autodetect
Intel 82801DB-ICH4 Modem-Modem
Intel 82801DB-ICH4 - IEC958
Intel 82801DB-ICH4 - ICH4
ALSA
ESD
OSS

The computer will play songs but will not produce any sound. I have never had a message telling me that there is no sound card installed, and i havent been able to find any Linux drivers for the sound card. Anyway help or suggestions would be appreciated.

first of all, only drivers is alsa which it seems you have installed

also try changing 1st and 2nd in some other nonmodem or iec, put third and last on alsa 
smth like this:
[[img]http://www.picturebay.net/img/guests/th/Bez_naslova.gif[/img]](http://www.picturebay.net/img/guests/Bez_naslova.gif)

---

### Post by Nicallen63 on 2007-12-22
I changed the first two to every option that was on the list and there was still no sound.

---

### Post by TheLions on 2007-12-23
had you tried unmuting from gnome alsa mixer? (programs-->add/remove-->"Gnome Alsa Mixer)?

---

### Post by Nicallen63 on 2007-12-23
Yes. I have tried unmuting everything that i could find that had a mute button, ive raised every level as well.

---

### Post by TheLions on 2007-12-24
if you have 4(or more) channel sound try connect your speakers in different jack, maybe in penguin front and back speakers are switched.

if that doesn't  work try recompile alsa

---

