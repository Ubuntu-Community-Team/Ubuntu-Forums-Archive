---
title: "Problem with sound"
date: 2015-09-25
forum: Hardware
---

### Post by ProfWoland on 2015-09-25
Hi, I've recently installed lubuntu on my pc and I have a problem with sound, when I play video or mp3, with player on in browser, it is too quiet like whispering and sound is volumed up to maximum, and also when I plug in headset sound plays on speaker and on headset, is there any way to fix that? The spiker is a built in into pc, and pc is old one if you want to post configuration on pc let me know, i'll post pictures.

Sorry for bad english...

edit: now I see that sound setting in bottom left corner of screen, doesn't have any function, it won't volume up or down sound level alway stay the same no matter what level is set 0 or 100 o.O

---

### Post by ajgreeny on 2015-09-25
I can't remember whether pulseaudio is a default package in Lubuntu but if you don't have it I suggest you install it along with pavucontrol (the pulseaudio volume control application).

Now in the Sound & Video menu you will see Pulse Audio Volume Control which may allow you to see what is set too low for your wishes.

You may also find alsamixer very useful.
Run command alsamixer in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;  some channels may not show until you scroll far-right.
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture" screen.
Esc will save and exit.

---

### Post by ProfWoland on 2015-09-25
I fixed it for some time with alsamixer, and later I can only play sound with headset, tried changing levels of everything and still nothing, when un plug headset sound wan't play

---

### Post by ajgreeny on 2015-09-25
Do you have pulseaudio, as I suggested?

---

### Post by ProfWoland on 2015-09-25
I've installed it but no changes, after i've changed some settings in alsamixer sound started playing on speaker, now it's everything ok with sound.
Thank you!

---

### Post by ajgreeny on 2015-09-25
Great!

Please mark SOLVED from the Thread Tools menu at the top.

---

