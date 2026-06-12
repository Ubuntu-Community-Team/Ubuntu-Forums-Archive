---
title: "mouse lags, freezing, bad sound quality"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Motomouse on 2009-09-05
I experienced mouse lags, freezing and bad sound quality on my Ubuntu Studio 9.04. :(

My 2 step solution: :D

1. mouse lag and freezing:

Moved from the realtime kernel to the generic kernel.

2. bad sound quality: 

Moved from pulseaudio to alsa


(Just a pointer for people with similar problems, search up existing bug reports in launchpad or existing detailed process descriptions)

---

### Post by dagoth_pie on 2009-09-05
Just to throw this out there, by swapping from pulse you will run into problems when you get more than one program to play sound (alsa and oss like to hog the sound card, pulse lets them run through it) if it's the only fix then you'll have to run with it, but keep it in mind...

As for the kernel... went way over my head :D

---

