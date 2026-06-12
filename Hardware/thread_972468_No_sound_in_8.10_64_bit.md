---
title: "No sound in 8.10 64 bit"
date: 2008-11-05
forum: Hardware
---

### Post by claudius753 on 2008-11-05
So I had 8.10 32 bit installed, and I had sound though the volume was very low.

I just installed 8.10 64 bit in order to be able to access the full 4 GB of ram in my machine.  However, now I have no sound at all.

lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Device 00a0
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at d0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Alsamixer is all unmuted and volume is set to 100, but when I do the System > Preferences > Sound test, I get nothing at all.  I have no idea what is up.

---

