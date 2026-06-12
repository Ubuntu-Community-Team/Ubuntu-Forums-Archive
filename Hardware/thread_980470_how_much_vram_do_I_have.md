---
title: "how much vram do I have"
date: 2008-11-12
forum: Hardware
---

### Post by flyingsliverfin on 2008-11-12
I don't know how much vram I have, is there a way to find out? I run 8.10.

---

### Post by y@w on 2008-11-12
Not sure of a way to see it directly, but you can do an 'lspci' from the terminal and it will display the model of your video card. Then just use Google..

---

### Post by rwap on 2008-11-12
> **flyingsliverfin said:**
> I don't know how much vram I have, is there a way to find out? I run 8.10.
Run 

lspci -vv

In the terminal,

The output will be very long and it will have a section like this in it...

02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
	Subsystem: Hightech Information System Ltd. Device 2072
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at d0000000 (32-bit, prefetchable) **[size=256M**]
	Region 1: I/O ports at c000 [size=256]
	Region 2: Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx


I made where it says the size** BOLD** If you cant find it post the output...

---

### Post by flyingsliverfin on 2008-11-20
thax

---

