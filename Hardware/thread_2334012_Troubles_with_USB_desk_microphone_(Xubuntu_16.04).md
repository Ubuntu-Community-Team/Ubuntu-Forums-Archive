---
title: "Troubles with USB desk microphone (Xubuntu 16.04)"
date: 2016-08-15
forum: Hardware
---

### Post by Guyofdoom42 on 2016-08-15
I'm having some trouble with a USB microphone. Pulseaudio recognizes it, and is showing input from it, but if I run ```
pactl load-module module-loopback
``` I can't hear anything. In Audacity, it doesn't see the Microphone as an available input, but Steam and SimpleScreenRecorder allow me to take input directly from it.

This microphone worked perfectly under Linux Mint, I don't see why it doesn't work now.

If anyone could help, that would be greatly appreciated. Thanks!

---

### Post by ajgreeny on 2016-08-15
have a look in the audacity ->Edit ->Preferences to see what is showing in Devices ->Recording.

My screenshot shows how mine is set for a normal mic with a 3.5mm jack plug, using pulseaudio.  I don't have a USB mic to test but this may give you some ideas to think about.

---

