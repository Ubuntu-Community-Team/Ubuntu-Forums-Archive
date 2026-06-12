---
title: "Recording noise and clipping (Intel Corporation 82801G (ICH7 Family))"
date: 2009-01-25
forum: Hardware
---

### Post by schuellerf on 2009-01-25
Hi!
I hope I'm posting this in the right category. I've got a Laptop with Ubuntu and the most things I need now are working. Even the sound via alsa/Pulseaudio is working with one big problem.
Playback works perfectly and when recording (audacity, skype, gnome-sound-recorder) there is a massive background noise. No matter if using the internal mic. or an external. It is working with vista with both mics. 
I already tried serveral things like disabling pulseaudio, removing alsa and using oss...  its always the same - playback fine - recording heavy noise...

the recorded sound seems to be clipped (like if overamplified) - also if I reduce the recording volume...

can anyone help me?
(the output below is enough for the beginning right?)


my alsa-info output is
[http://www.alsa-project.org/db/?f=1352e48aec435397da3e3f691eae74e9e288f74c](http://www.alsa-project.org/db/?f=1352e48aec435397da3e3f691eae74e9e288f74c)
(it says pulseaudio is not running - but it is...)

lspci -v says
[...]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 8c000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[...]

btw. its a Toshiba Qosmio laptop

---

