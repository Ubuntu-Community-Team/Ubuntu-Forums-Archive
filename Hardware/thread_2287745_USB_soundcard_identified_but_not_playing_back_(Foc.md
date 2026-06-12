---
title: "USB soundcard identified but not playing back (Focusrite Scarlett 8i6)"
date: 2015-07-22
forum: Hardware
---

### Post by leee2 on 2015-07-22
Hi all,

As the title says, I have a sound card that shows up in `/proc/asound/cards` and `aplay -l` - but I am unable to have it play. This is a very fresh install of trusty, and I am unable to select it in the GUI (unity) system settings menu, since it doesn't appear there.

Attached is `speaker-test` and `aplay -l`.

---

### Post by Garey on 2015-07-23
Hello, i have same sound card (8i6) and got it work with this guide: [http://dragly.org/2014/01/12/focusrite-scarlett-2i2-flawlessly-working-on-ubuntu-with-jack/](http://dragly.org/2014/01/12/focusrite-scarlett-2i2-flawlessly-working-on-ubuntu-with-jack/) 
Try to sink it with jack (with pulseaudio-module-jack), if you got some problems, post it to this thread.

---

