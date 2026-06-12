---
title: "[SOLVED] Sound disappeared, get static on laptop"
date: 2008-11-18
forum: General Help
---

### Post by LeeLgrqst on 2008-11-18
I have a Gateway mt3422 laptop.  I just moved from Windows Vista to Ubuntu 8.10 64, so I am just starting to learn how to use this OS.

So when I first installed it, the sound worked.  Then one day I went to play a CD and discovered that the sound didn't work anymore.  The only thing that happens is a crackle sound coming from the speakers.

I tried this, which I found in another post from this site:
sudo killall pulseaudio
sudo alsa force-reload
and then go to System>Preferences>Sound and change everything to ALSA

It didn't work. I've been searching for days on how to fix the problem, but I don't know what to do.

---

### Post by LeeLgrqst on 2008-12-12
Solved - I found this in another post finally.

I had to right click on the speaker icon on the panel.  Click on the Open Volume Control and turn up the PCM and Capture Mux.

---

