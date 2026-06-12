---
title: "Midi keyboard"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by ooZAFLE on 2006-06-13
hello all
I've tried to get my m-audio radium 49 working with only partial success.
basically i can start up rosegarden and when i hit the keys on my keyboard i can see the levels move around but there is no sound.

I've tried using differnt drivers such as the midisport drivers with no success and i'm pretty sure i've modprobed all relavent modules in the system. I opened up alsamixer and turned all the volumes up and unmuted everything just to be sure, then set the capture volumes up. When i look in /proc/asound/ it shows my keystation board is there. Am i completely overlooking something simple or what? Any tips or advice would be extremely appreciated. I don't really want to take this back. thanks

---

### Post by ooZAFLE on 2006-06-14
i figured it out.
it was basiacally just some jack connections. it still only works with one program and i can't get sound output from Rosegarden4.

---

