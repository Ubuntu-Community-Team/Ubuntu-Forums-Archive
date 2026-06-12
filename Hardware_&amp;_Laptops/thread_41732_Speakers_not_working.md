---
title: "Speakers not working"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by Pi rules on 2005-06-14
I just installed Ubuntu Linux on a dual-boot computer with Windows XP about 2 days ago and I haven't heard any sound while on Ubuntu since.  I followed the instructions at ubuntuguide.org, but they didn't help.  I also went on Alsa Mixer and didn't see anything wrong.  On the volume controls, everything looks right, and it found my device (C-Media Electronics CMI9761) and the volume meter shows the volume correctly, but I do not hear anything from the speakers.  I checked that my speakers were on the correct port, I tried other speakers, and both speakers work on Windows XP.  I would appreciate any help.

---

### Post by akinwale on 2005-06-14
Wow... I have the exact same chip as you: CMI9761. I got no sound with Hoary Hedgehog but there's sound with Warty Warthog. I guess it's possible there's a problem with the ALSA release. I tried recompiling alsa-driver 1.0.8 according to the instructions in the "Hoary Sound Broke?" thread but still no sound.

I also tried compiling alsa-driver 1.0.5 (the one that comes with Warty Warthog) but I get errors as a result of some memalloc C source file somewhere (kernel headers, I guess), but I don't recall now. I just gave up and I'm currently working with a soundless system :)

Can/will this be fixed?

It'll be nice

---

### Post by Pi rules on 2005-06-24
I got my sound to work...finally.  I muted IEC958 Capture Monitor with Alsa Mixer GUI, and now I have sound, and I didn't even have to reboot.

---

### Post by edward sick on 2007-11-19
mine dont work. damn this sucks

---

