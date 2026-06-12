---
title: "Karmic: High freq noise"
date: 2009-12-08
forum: Hardware
---

### Post by nedwed on 2009-12-08
Hi Guys,
I switched from 8.10 to 9.10 and as a lot of you I came across the pulseaudio problems.It's really bugging me, because the 8.10 version worked perfect.
First problem was the cracking sound in the speakers, which was easily solved by commenting out:
options snd-hda-intel power_save=10 power_save_controller=N
in the alsa-base.conf.
Second problem is really annoying and I don't know how to solve it.
There is a strange high frequency noise in my speakers. During playback everything is fine. After few hours of working on my laptop the noise is really killing me.
Changing PCM levels, mute - no effect.
Switching off pulseaudio - no effect.
Of course my user.log is full of pulseaudio errors. Any hints?

---

