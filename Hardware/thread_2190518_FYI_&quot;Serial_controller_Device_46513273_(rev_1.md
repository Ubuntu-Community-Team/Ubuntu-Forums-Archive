---
title: "FYI: &quot;Serial controller: Device 4651:3273 (rev 10)&quot; recognized"
date: 2013-11-27
forum: Hardware
---

### Post by sanderj on 2013-11-27
I just got a dual serial port PCI card from Hongkong. It seems Ubuntu 13.10 does recognize it. As I don't see the lspci anywhere on Google, I thought I would share this:

lspci & uname & dmesg:

```
05:01.0 Serial controller: Device 4651:3273 (rev 10)

Linux MegaTurbo 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


$ dmesg | grep -i tty
[    0.000000] console [tty0] enabled
[    0.532023] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.533521] 0000:05:01.0: ttyS4 at I/O 0xbc00 (irq = 22) is a XScale
[    0.533651] 0000:05:01.0: ttyS5 at I/O 0xb880 (irq = 22) is a XScale
[   18.989633] Bluetooth: RFCOMM TTY layer initialized


05:01.0 Serial controller: Device 4651:3273 (rev 10) (prog-if 02 [16550])
	Subsystem: Device 4651:3273
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at bc00 [size=8]
	Region 1: I/O ports at b880 [size=8]
	Kernel driver in use: serial



```

Not yet tested with an actual serial device.

---

