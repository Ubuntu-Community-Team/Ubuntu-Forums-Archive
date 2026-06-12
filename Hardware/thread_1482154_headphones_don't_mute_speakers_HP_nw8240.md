---
title: "headphones don't mute speakers HP nw8240"
date: 2010-05-13
forum: Hardware
---

### Post by rmdnet on 2010-05-13
Hi,

I have a HP nw8240 and it runs great with Ubuntu 10.04 but when I plug in the headphones the speakers don't mute.

This is the output of lspi -v

[FONT="Courier New"]00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0934
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3100 [size=256]
	I/O ports at 3200 [size=64]
	Memory at c8c01000 (32-bit, non-prefetchable) [size=512]
	Memory at c8c02000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0[/FONT]


Any ideas?

Thanks in advance

---

### Post by dino99 on 2010-05-13
gnome-alsamixer might help

---

