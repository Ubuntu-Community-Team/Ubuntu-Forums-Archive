---
title: "Lubuntu 12.04 headphone hiss problem"
date: 2012-05-04
forum: Hardware
---

### Post by mgfarley on 2012-05-04
I've just installed Lubuntu 12.04 on my Dell Mini 9 (inspiron 910). When I plug in my headphones, the internal speaker starts to hiss. It stops hissing as soon as I unplug my headphones. The audio from both the speaker and headphones is fine (apart from the hiss).

In the past I've used Lubuntu 11.04 and Ubuntu 10.04 LTS. The speaker hiss problem has happened after each install but I've always fixed it by adding the line 'options snd-hda-intel model=toshiba' to the alsa-bass.conf file (/etc/modprobe.d/alsa-base.conf), saving the file and then rebooting my laptop.

However with lubuntu 12.04 this solution hasn't worked. I've tried a couple of other models (including dell and auto) but this hasn't made any difference.

---

### Post by felichas on 2012-07-22
I just happened to read this today, that may very well be of interest to you.
[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

Look at point *4. Don’t try different “model” strings*

Good luck!

---

