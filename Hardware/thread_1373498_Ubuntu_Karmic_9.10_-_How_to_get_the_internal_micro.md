---
title: "Ubuntu Karmic 9.10 - How to get the internal microphone working on Dell Adamo 13"
date: 2010-01-05
forum: Hardware
---

### Post by adamouser on 2010-01-05
Hi guys

Ive been trying to get my audio output and microphone to work on my adamo with ubuntu 9.10. there are threads telling you how to get your output to work. i leave this part out since i think i messed around a lil bit ;)

short story AUDIO OUT:
 * completely uninstalled PulseAudio packages => now im no longer able to use the hardware volume control and the Volume Control App in the panel is also gone. System - Preferences - Sound does no longer respond either since these are obviously all listening to PulseAudio
 * Upgraded my Alsa v1.0.21 via a script from "soundchecker". You can find it easily in the forums
 * added the following line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=dell-m6
```
AUDIO IN:
 * run ```
alsamixer
``` and hit F4 to display the capture devices
 * in my case the devices were wrongly labeled => the DIGITAL device was the mic that worked.

Here is my config that got my mic to capture without too much noise. Play around for yourself to get the config that fits the most for you...

[IMG]http://img12.imageshack.us/img12/6848/alsamixer.gif[/IMG]

---

### Post by arsham on 2010-03-10
Thanks
That solved my problem too
I think the key was digital mic

---

