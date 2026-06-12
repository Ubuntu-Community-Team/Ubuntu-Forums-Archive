---
title: "No sound from Nvidia HDMI with PulseAudio"
date: 2013-07-31
forum: Hardware
---

### Post by halfbeing on 2013-07-31
I just installed UbuntuStudio using a TV attached via HDMI to an Nvidia card for graphics and sound. Unfortunately no sound happened. When I played a video the volume meter showed that someone thought sound was going somewhere, but the speakers were silent. I then found that[INDENT]
aplay -D hw:1,7 /path/to/a/soundfile.wav[/INDENT]

did produce a sound. So I edited /etc/pulse/default.pa to comment out the section with "load-module module-udev-detect use_ucm=0" and added the line

[INDENT]
load-module module-alsa-sink device=hw1,7
[/INDENT]

and now pulse won't start at all. I get the following lines in the output when I try to run it:

[INDENT]
(   0.009|   0.001) D: [pulseaudio] alsa-util.c: Trying hw1,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.010|   0.001) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hw1,7
(   0.010|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw1,7: No such file or directory

[/INDENT]
So if device hw:1,7 exists and is accessible to ALSA, why can't I get PulseAudio to see it? How can I get sound working through the HDMI port?

[INDENT][SUB][/SUB][/INDENT]

---

### Post by Yellow Pasque on 2013-07-31
```
device=hw1,7
```
You missed a colon  hw**:**1,7

---

### Post by halfbeing on 2013-07-31
> **Temüjin said:**
> ```
device=hw1,7
```
You missed a colon  hw**:**1,7

So I have!!!!! Thank you!

---

