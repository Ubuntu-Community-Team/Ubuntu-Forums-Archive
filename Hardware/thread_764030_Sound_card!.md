---
title: "Sound card!"
date: 2008-04-23
forum: Hardware
---

### Post by sammi.jo on 2008-04-23
Help!

My soundcard just stopped working; I used to have sound, even on this install, but nothing seems to be working. I've tried purging and reinstalling alsa to no avail, and I've got this when I do lspci -v

> 04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Unknown device 1e40:1509
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c9100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

1) what does the access denied bit mean? Do I need access for this to work? How would I do it?

2) If I don't need access, can anybody please help me fix this?




---------- 

Solved with sudo apt-get install linux-386

---

