---
title: "Audio driver issues- Mic input routes directly to speaker"
date: 2011-04-21
forum: Hardware
---

### Post by spinsane on 2011-04-21
I'm running an Asus x83Vm x2.

Ever since a somewhat recent update (around the jump to the .28 kernel), the audio driver has gone wonky. The problem is kind of odd-- My microphone comes on during boot and routes all of the information it receives directly to the speakers. This, of course, causes feedback and makes an intolerably high-pitched screeching noise.

The error happens as soon as drivers are loaded, before the plymouth splash screen even comes up.

AlsaMixer shows that the Mic isn't even active. Killing pulseaudio doesn't do anything.

This is my alsa report thingy.
[http://www.alsa-project.org/db/?f=093325b83633ace16e72160853e92be516fb4d1c](http://www.alsa-project.org/db/?f=093325b83633ace16e72160853e92be516fb4d1c)

I've had 10.10 on this machine the day it was released, so it is definitely a new problem.

---

