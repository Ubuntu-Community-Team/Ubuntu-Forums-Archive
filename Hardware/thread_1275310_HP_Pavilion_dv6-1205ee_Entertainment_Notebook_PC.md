---
title: "HP Pavilion dv6-1205ee Entertainment Notebook PC"
date: 2009-09-25
forum: Hardware
---

### Post by RoMiONeT on 2009-09-25
Hello

i'm using ubuntu 9.04 .. and there is no any sound output  , when i play sound file i can't here any thing .. there is no sound also i fine the sound icon panel ..

sound card :  Audio Playback SRS Premium Sound
3D Sound Blaster Pro compatible sound 16 bit integrated.

»  IDT High-Definition Audio CODEC Driver  


Thanks

---

### Post by RoMiONeT on 2009-09-26
up

---

### Post by anonymtrk on 2009-10-08
Download latest alsa drivers and install it. Thats the solution. :)

---

### Post by Yellow Pasque on 2009-10-08
Upgrading ALSA may or may not be necessary.

The first thing to try is:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this to end:
```
options snd-hda-intel model=hp-dv5
```
Save. Quit. Restart system.

If that doesn't work, then try upgrading ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

