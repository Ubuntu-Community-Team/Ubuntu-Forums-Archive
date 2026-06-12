---
title: "Mic doesn't work, doesn't seem to be even seen by ubuntu 8.10"
date: 2009-01-29
forum: Hardware
---

### Post by KungFuGeek on 2009-01-29
When i was running 8.04 my mic worked beautifully. Then when i backed up everything and did a clean install of 8.10 my mic stopped working, and i've been off and on trying to fix it for a while now and can't seem to figure it out.

Not sure what all info would be needed to help, but here is an lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01d2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I used to have a setting in alsamixer for front mic, but now all i have is playback and capture(neither of which are muted).  I can't record in audacity, sound recorder, and i can't talk in skype.

Thanks in advance.

---

### Post by slimx3m on 2009-04-13
i am having the same problem. if i find a solution i'll let you know.

---

