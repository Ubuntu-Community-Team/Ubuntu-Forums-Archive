---
title: "Capture Card  - DC10+ help"
date: 2012-04-23
forum: Hardware
---

### Post by espo111 on 2012-04-23
I have a very old Pinnacle DC10+ capture card I want to use with Ubuntu studio to try and capture some old VHS tapes (before they disinigrate).

I put the card in and it "seems" to be recognized (at least as far as I can tell.

but I have no idea how to get it working otherwise. I have tried xawtv but this does not work. Same with KDEnlive.


so my questions are... can someone give me a clue as to use it?  the driver is installed it seems, but no luck yet. What is thge best application to try and capture with. I also found some posts that use video4linux, but have no idea how to see if it is being used.

can someone help me find out where I am in the process of gettingit to work?

any help at all would be greatly appriciated as my only other option is to go back to  Windows XP :(

thanks

Dmesg
```

23.912073] Linux video codec intermediate layer: v0.2
[   23.919375] Linux video capture interface: v2.00
[   23.921007] Zoran MJPEG board driver version 0.10.0
[   23.921083] zr36067 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.921087] MJPEG[0]: Zoran ZR36067 (rev 2), irq: 22, memory: 0x50000000
[   23.921090] MJPEG[0]: Subsystem vendor=0x1031 id=0x7efe
```




lspci

```
05:01.0 Multimedia video controller: Zoran Corporation ZR36057PQC Video cutting chipset (rev 02)
	Subsystem: Miro Computer Products AG DC10 Plus
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: zr36067
	Kernel modules: zr36067
```

---

### Post by espo111 on 2012-04-24
um... ok then. Back to windows xp :(

---

