---
title: "Sound input not capturing in 9.04"
date: 2010-04-02
forum: Hardware
---

### Post by unteer on 2010-04-02
Ok Ubuntu Forums peeps, I am hoping the collective knowledge of these forums defeats my googling and helps solve me infuriating sound problem.  First off here's the system skinny:

Lenovo IdeaPad S9e
running Ubuntu 9.04 with 2.6.28 generic kernel
Sound Module: snd-hda-intel
Sound Hardware: -Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
                          -ALC269 Analog chip


I know there are some issues with Ubuntu and this specific audio chipset, but most of the issues I have noticed refer only to internal mics, not external.  I have now plugged in an external mic, and checked all my mic input levels, and volume controls are up at both the ALSA and PulseAudio levels.

When I boost the mic boost volume, I can even get a feedback loop running, so the hardware is all working.

But I am stuck.  The levels don't budge on either the pulseaudio manager applet, or the Sound Recorder application.  I have perfect sound output.

Can anyone confirm if its a bug with ALL mics on this particular audio chipset, or just the internal as bug reports have suggested and i am having different issues with the external mic.

Cheers!

---

