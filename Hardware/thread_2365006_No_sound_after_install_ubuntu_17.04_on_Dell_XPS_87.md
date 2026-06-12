---
title: "No sound after install ubuntu 17.04 on Dell XPS 8700 Desktop"
date: 2017-07-01
forum: Hardware
---

### Post by sabraham2017 on 2017-07-01
After fresh install on ubuntu 17.04 on Dell XPS 8700 desktop, only "dummy output" device is shown on the sound settings and I am not hearing any sound.

> 
[http://www.alsa-project.org/db/?f=6c07d5fefbc3e857829823fd12458349af6d9059](http://www.alsa-project.org/db/?f=6c07d5fefbc3e857829823fd12458349af6d9059)


As per the instructions in another thread I tried 

options snd-hda-intel model=basic 
and 
options snd-hda-intel model=DELL8700

and > 


sudo alsa force-reload


Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer.


but that didn't help either.

---

