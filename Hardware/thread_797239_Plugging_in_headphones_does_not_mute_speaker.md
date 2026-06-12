---
title: "Plugging in headphones does not mute speaker"
date: 2008-05-17
forum: Hardware
---

### Post by Ouguiya on 2008-05-17
Greetings everyone.

I am seeking help, my problem is as follows:

When I plug in my headphone (into the green and red plugs), the sound continues to come from the internal speakers, the system more or less ignores the headphones.

As to the microphone, the situation is reversed: Linux cannot record the sound from the integrated microphone, only when something is plugged in.

I hope anyone can help me on this. I tried searching the forum and the internet. This seems to be quite a common bug, and has been heavily discussed, however, none of the solutions worked for me up till now.

Card is: HDA Intel (a very problematic card I understand...)
Chip is: Sigmatel STAC9872AK

Note: I already tried all the bugfixes which were proposed out there, things like adding lines to the Alsa-Base file, or starting alsamixer and swichting did not work. (actually, the option where you type alsamixer in the console, and then switch to headphone cannot be done by me, since there is no headphone option available, only MASTER and PCM)

I also tried doing things with volume control, but there is no other mixer than "master" available, so switching is not an option either.

I hope someone has a bugfix for this

Yours,

Ouguiya

---

