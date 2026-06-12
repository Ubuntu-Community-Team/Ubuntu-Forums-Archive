---
title: "via 8237 audio is silent, but works in knoppix"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by burlap on 2005-07-07
Just to finish this thread:
- There is something wrong with Ubuntu sound management (well, there is this big thread on hoary sound, so I should have felt warned...).
- There is something wrong with via 8237 drivers.
- I haven't paid attention to all the changes I made: big mistake, as I can't really reproduce all the steps. 

And finally (almost) everything works: alsa mixer (via 8237) controls volume, however master and pcm are still in this strange "no sound" state. "via dix" works as a proper device...

---- OLD ----
When I was trying to solve problems with audio I rebooted each time I changed something (I couldn't figure out snd modules interdependencies to unload them all...). It didn't help. I switched the computer on today and suddenly sound works... (I hate this: I can't even tell what was the last change I made). 

However it is not possible to manipulate sound volume (screenshot attached). In gnome-panel volume-control provides choice between C-media (OSS Mixer) and via 8237 (alsa mixer). With via I can change volume on the panel, but it does not actually change. In C-media it is not possible to increase/decrease volume: possible choices are mute or full. What can I do?

---- EVEN OLDER ----
The title says it all: via 8237 (c-media cmi9761) does not work in hoary. I've tried different sets of configs (including libesd and libesd-alsa), using alsa drivers from universe and fresh from alsa project site (1.0.9b compiled for via82xx cards): nothing helped. Maybe I missed something? 

I have tried in knoppix - older one running on 2.4.x - and this card WORKS! It seems that old oss drivers (I can double check it, but it didn't look like alsa) are more effective... 

My questions: (I have searched this forum and haven't found any success stories) 

- is it possible to make onboard via 8237 running with alsa on Hoary? 
- if not, how to use oss drivers instead? 

(BTW: in alsamixer master and pcm are unmuted but it is not possible to inrease their volume. It is possible to play with other settings (center, lfe), but no sound is heard anyway...).

---

