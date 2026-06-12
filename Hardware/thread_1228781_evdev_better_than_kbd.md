---
title: "evdev better than kbd?"
date: 2009-08-01
forum: Hardware
---

### Post by fela on 2009-08-01
I've been having some keyboard problems ever since I started using Ubuntu 9.04. Basically the modifiers aren't working properly, they're temperamental. For example if I hold alt to move the window without the title bar, sometimes it doesn't 'recognize' that I'm pressing alt and just selects an element in the window. But then, if I hold alt for a bit longer say, it starts working again.

Well, needless to say I looked through my /etc/X11/xorg.conf, and there it was: in the keyboard section the driver was kbd, I'm pretty sure I was using the evdev driver before 9.04, and lo and behold, when I changed to the evdev driver (just thought what the hell and replaced 'kbd' with 'evdev'), it started working a bit better again. Still not as good as it was in 8.10, but I think that's more due to my degrading wireless keyboard (too much call of duty I expect xD).

Does anyone know what the reason for this change is, and why kbd was giving me bad performance/bugs? I have a PS/2 wireless keyboard (labtec).

Thanks :D

EDIT: Nope, turns out the keyboard/mouse combo is just as buggy with evdev. I wonder what the matter could be...

---

