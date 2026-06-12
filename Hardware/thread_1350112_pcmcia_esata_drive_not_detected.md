---
title: "pcmcia esata drive not detected"
date: 2009-12-09
forum: Hardware
---

### Post by lbharti on 2009-12-09
I have tested it in windows on the same system and the esata hot plug works. In Ubuntu 9.10, the pcmcia card is detected as SATA_VIA, which it is, but on plugging the hard drive, the drive does not show as connected. Here is the lspci -v output for the controller:

RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 4420 [size=16]
	I/O ports at 4430 [size=16]
	I/O ports at 4440 [size=16]
	I/O ports at 4450 [size=16]
	I/O ports at 4400 [size=32]
	I/O ports at 4000 [size=256]
	Expansion ROM at f4000000 [disabled] [size=64K]
	Capabilities: [e0] Power Management version 2
	Kernel driver in use: sata_via
	Kernel modules: sata_via

On plugging there are not any events logged in dmesg.

Before all this an incident happened. The first time, I plugged in the hard drive, it was detected, but while copying some data, the system got stuck, and I had to reboot it. Since then, I have not been able to see a disc detection in the logs.

What should I do?

---

