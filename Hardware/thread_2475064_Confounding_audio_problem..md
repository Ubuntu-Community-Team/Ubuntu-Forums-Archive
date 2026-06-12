---
title: "Confounding audio problem."
date: 2022-05-15
forum: Hardware
---

### Post by MartyBuntu on 2022-05-15
On Ubuntu 18.04, just yesterday the audio fell apart. Not after an update or any hardware change, just after a boot the quality fell apart.
The audio is low and squeaky when it works and only a single audio channel works, or a single audio channel (usually left) is played as a mono file over both channels.
Sometimes I play an mp3 or .wav file and drag the slider forward (using many different media players) and different sequences play out at different times, in bad quality.
It gets weird....here's what I've tried:
- Two different LiveUSB's...exact same poor quality
- Two different external USB audio hardware devices, same quality
- Three different earphone and one different set of external speakers
- Connected to the front panel audio jack (Asrock B450 PRO motherboard)...and directly to the rear audio panel jacks...same
- Upgraded kernel...makes no difference
- System updates...nothing changes
- Unplugged any unnecessary peripherals....same
- No electrical interference...tried different wall outlets
- All manner of audio cables...swapped
- Went into BIOS and made sure onboard HD audio was selected....same
- Both Pulseaudio and JACK, which I've always been able to use, return the same squeaky poor audio

NOW HERE'S WHAT WORKS!
**Bluetooth Audio**
Any Bluetooth audio interface (headphones and speaker) are able to reproduce perfect sound.
What is going on and what can I do to trace this problem?

---

### Post by MartyBuntu on 2022-05-15
Problem solved.
My Behringer USB audio interface is malfunctioning, and just being connected to the system it will drag it down. Unplugged it and the problem disappeared.
Time to find a new USB audio interface.

---

