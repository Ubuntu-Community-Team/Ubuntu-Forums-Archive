---
title: "Standard audio device change automatically from external sound Amp to HDMI."
date: 2019-11-03
forum: Hardware
---

### Post by jasper99 on 2019-11-03
Have Beyer A 200 p sound Amp, the output change every time to HDMI out. Is there way to lock sound output to A 200 p?

---

### Post by CatKiller on 2019-11-03
Gnome's sound controls are quite limited in their functionality. However, there are PulseAudio utilities in the repositories - I can't remember the name off the top of my head - that will allow you to set the default sound device, and optionally turn off the others.

---

### Post by philhughes on 2019-11-05
It's probably this bug. The workaround described in the bug report fixed it for me.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570)

---

