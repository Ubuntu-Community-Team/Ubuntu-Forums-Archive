---
title: "Plantronics headset: mic not recognized"
date: 2011-10-01
forum: Hardware
---

### Post by elbows on 2011-10-01
I have a Plantronics 995H headset. On my laptop, running 10.04 netbook remix, the headset is recognized and audio output works, but I don't have an option to use the microphone for input.

In Sound Preferences->Hardware, the headset shows up and list "Analog Stereo Output + Analog Mono Input". In Sound Preferences->Output it appears in the device list and I can direct sound to it. However, in Sound Preferences->Input it doesn't show up -- only the internal microphone is listed.

On my desktop running 10.10, the headset shows up in both the Input and Output tabs and works fine. But I'd like to avoid upgrading the laptop if possible.

---

### Post by elbows on 2011-10-07
Since nobody had any ideas about this, I eventually did some digging into Pulse Audio myself. 

It turns out that sometimes the headphones are recognized, and other times the microphone is recognized -- but never both at once. The devices are missing from paman as well as the Sound Preferences dialog.

I eventually found the answer here: [http://fedoraproject.org/wiki/How_to_debug_PulseAudio_problems](http://fedoraproject.org/wiki/How_to_debug_PulseAudio_problems), in the "Sound Devices Not Visible in paman" section. As near as I can tell system-wide Pulse Audio config is trying to load module-hal-detect, which apparently doesn't exist. So it falls back to module-detect, which is deprecated and apparently doesn't work very well.

Replacing module-hal-detect with module-udev-detect, as suggested on that page, fixed everything.

---

