---
title: "No sound?"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by Gibbz on 2004-12-01
well, kinda, i get sound in xmms and thats it, before i was getting sound but i tryed to install the nvidia drivers and it couldnt install correctly, and must have changed something...

for some reaosn i get sound in ut2k4, xmms, quake 3, wolfET and thats all, no more ubuntu system sounds or sound in doom....


anyway when running doom 3 i get,...

dlopen(libasound.so.2)
asoundlib version: 1.0.5
Alsa is available
------ Alsa Sound Initialization -----
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: No such device
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------


EDIT: sound in ut2k4 is working, but there is a loud screetchign sound louder the the game sounds/music...

---

### Post by Moobert on 2005-01-04
doom 3 doesn't seem to surport alsa that well, and it uses it as standard. The game will loads there when using the alsa, but the sound is distorted and the fps takes a real hit. So the best way to fix seems to be to swap to the oss drivers, ubuntu uses both oss and alsa you will have them. To use the oss sound drivers run doom 3 with: 

doom3 +set s_driver oss

---

