---
title: "Joystick and Ubuntu 9.10"
date: 2010-01-13
forum: Hardware
---

### Post by Racecar56 on 2010-01-13
I can't seem to get my joystick working. It doesn't seem to get detected, as there is no /dev/jsX or /dev/input/jsX (X is any number including 0).

The joystick is a Gravis Destoyer 10501 and is plugged into the GamePort at the back of my computer provided by a PCI sound card I grabbed from my expansion card collection.

Sound card's lspci -vvnn output:
01:00.0 Multimedia audio controller [0401]: Avance Logic Inc. ALS4000 Audio Chipset [4005:4000]
Subsystem: Avance Logic Inc. ALS4000 Audio Chipset [4005:4000]

The joystick is plugged in all the way. I don't think there is anything wrong with the sound card or the joystick. The sound card seems to work quite nicely.

I can post more information/specs if you need them.

I have the snd_als4000, analog, and gameport modules loaded.

---

