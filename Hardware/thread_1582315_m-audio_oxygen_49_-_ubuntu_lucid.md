---
title: "m-audio oxygen 49 - ubuntu lucid"
date: 2010-09-26
forum: Hardware
---

### Post by dharmagio on 2010-09-26
I have my system all workout to handle rt audio and everything works fine, but i used to work with my piano keyboard m-audio 49 in earlier ubuntu versions and now i am not being able to use it in ubuntu lucid! 

when i try to use it in energyxt and check the box for oxygen49 the program breaks down and it gives this lines on terminal,

ALSA lib ../../../src/rawmidi/rawmidi_hw.c:100:(snd_rawmidi_hw_params) SNDRV_RAWMIDI_IOCTL_PARAMS failed: Invalid argument
energyXT: ../../../src/rawmidi/rawmidi.c:264: snd_rawmidi_open_conf: Assertion `err >= 0' failed.
Aborted

______________
plus i have MidiSport and fxload installed
using kernel 2.6.31-11-rt
it doesnt work with non rt kernel either


can anyone help? thanks

---

