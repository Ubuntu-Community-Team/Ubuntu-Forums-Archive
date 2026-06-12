---
title: "hp ir remote"
date: 2009-02-19
forum: Hardware
---

### Post by Dawei87 on 2009-02-19
just curious, ive been at it for hours now. has anyone gotten the hp ir remotes to work with lirc? im a newb and i have had no luck whatsoever figuring this out

---

### Post by remu on 2009-02-21
I have a HP dv4, and I have the same issue. I can't get the remote that came with my laptop working under Ubuntu. I dual boot and have Vista installed as well, and under Vista, it works just fine. Does anyone know how I may be able to fix this?

---

### Post by epidemiks on 2009-02-21
are you using Ibex?
my friend just got a dv4, and the remote worked straight out of the box (except for ff & rw) on 8.10

---

### Post by Dawei87 on 2009-02-22
i am using ibex. my laptop is a dv5. i remember on a fresh install it didnt work at all, then after another fresh install it did (just volume) and now it doesnt work at all. im not sure what changed. if anyone has a good how-to for lirc, that would be great. ive been researching it but it seems way over my head

---

### Post by Dawei87 on 2009-02-27
i got it to work by downloading lirc, and everything else in synaptic that had lirc in the name (5 or 6 packages) and then without setting up lirc my remote became fully operational! i may have opened the lirc properties and selected my ir port before it started working though. since then i did one more fresh install of ubuntu and the remote works out of the box again, all buttons. i also read somewhere that a bios update will fix this problem for most people.

---

### Post by fmfrisch on 2009-02-28
i downloaded lirc and got my pavillin hp remote to work partly. So started playing around with different remote drivers and realized that there was no difference. So i uninstalled lirc rebooted and my remote is still partly working! Is there IR support built Ibex?

---

### Post by abhiroopb on 2009-03-01
my remote works great for JUST listening to music. I can play/pause rewind, forward, stop and volume controls. However, I can't use it to start my music player of choice (songbird) or do anything else. Is there any way to programme the rest of the buttons?

---

### Post by Dawei87 on 2009-03-02
the only way i found to program the buttons without lirc was to go to keyboard shortcuts and set them there. you can set it to launch your default media player from there, and then you can set your default media player to whatever. thats the only way i know how

---

### Post by abhiroopb on 2009-05-04
I was wondering if the HP remote could be configured to work with VLC? I'm not sure how to use LIRC, etc.

---

### Post by Dawei87 on 2009-05-04
it can but vlc uses its own shortcuts. you can open vlc and under settings find the key bindings and change them to your remote shortcuts. i actually dont think i could get it to work with multimdeia keys, (play,pause) so i used enter for play/pause and the arrows for fast-forward

---

### Post by abhiroopb on 2009-05-05
Yes I've got hotkey's setup but I would like to use my remote.

---

### Post by Dawei87 on 2009-05-05
well, my "OK" button on my remote is read as "enter" by keyboard shortcuts. So i set the keyboard shortcuts in vlc to use "enter" as "Play/Pause". then i was able to use the "OK" button on my remote to pause and resume the video in vlc. then i set it to fastforward and rewind using the arrow keys left and right. if you open up the keyboard bindings in vlc, you should be able to just highlight play/pause and keep pressing buttons on your remote until you find one you like that works. but vlc will not work with the multimedia keys afaik.

---

