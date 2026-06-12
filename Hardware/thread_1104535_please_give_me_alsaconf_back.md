---
title: "please give me alsaconf back"
date: 2009-03-23
forum: Hardware
---

### Post by kozuscek on 2009-03-23
Hi there.


On several machines, I'm having sound problems:
 - on my desktop machine, the cinelerra video editor will, from time to time, cause the audio driver to loop a shot audio segment (like 3/10s of a second long) to infinity. Cinelerra will then crash. All audio apps stop working, killing X does not help, and only unloading the sound module / rebooting helps. The sound card is a cmedia AC97-compatible card, integrated on the motherboard.
 - on my laptop, my sound card is incorrectly detected as Pulse audio (card #0, card #1 is my Intel hda), and the peak volume is noticeably lower (at least 20dB) that in windows. This is a major irritation. On top of that, the above-mentioned problem also occurs. I've previously-used Gentoo, and I've never had either of those problems, ever.

Now I've searched for alsaconf to set my audio card proper, but it wasn't anywhere in the path (which alsaconf), nor is it in any package (packages.ubuntu.com search). I finally read on some forum post the Ubuntu had removed it, because "they feel the is no use for it anymore". 

Well I want it back. What's the quickest way, short of compiling the entire ALSA stack by myself?

thanks all!


specs:
 - desktop: 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8152
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at b400 [size=256]
	I/O ports at b000 [size=64]
	Memory at f9fff800 (32-bit, non-prefetchable) [size=512]
	Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

 - laptop:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by tturrisi on 2009-03-24
apt-get install alsa-utils

---

