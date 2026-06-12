---
title: "how do i know if my pcmcia slot is on?"
date: 2008-05-11
forum: Hardware
---

### Post by j_dunavin on 2008-05-11
i have tried a few different versions on ubuntu, and none seem to recognize my pcmcia slot. So how do i even know if it works? I mean the thing just might not work. I am trying to use a usb/ firewire adaptor. It actually did work once, but i couldn't tell you when or how. 
So what commands can i use to see what is there, if it recognizes it, and how to use it??
thanks
joe

---

### Post by j_dunavin on 2008-05-11
ok typed this and got this.. sorry i am new
access denied? it would seem that it works?? but how do i get through to it??
joe@joe-laptop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Region 0: Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 00c8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at f4f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
	Subsystem: Dell Unknown device 00c8
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (2750ns max)
	Region 0: Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
	Region 1: Memory at f4f00000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Latitude C640
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 4: I/O ports at bf80 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
	I/O behind bridge: 0000e000-0000ffff
	Memory behind bridge: f6000000-fdffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Latitude C640
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at bfa0 [size=16]
	Region 5: Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Cirrus Logic Crystal WMD Audio Codec
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 5
	Region 0: I/O ports at d800 [size=256]
	Region 1: I/O ports at dc80 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: PCTel Inc Dell Inspiron 2100 internal modem
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 5
	Region 0: I/O ports at d400 [size=256]
	Region 1: I/O ports at dc00 [size=128]

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
	Subsystem: Dell Unknown device 00c8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2500ns min, 2500ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at ec80 [size=128]
	Region 1: Memory at fafffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at f6000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
	Subsystem: Dell Unknown device 00c8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f6020000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 24000000-27fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 0000e000-0000e0ff
	I/O window 1: 0000e400-0000e4ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
	Subsystem: Dell Unknown device 0005
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=8K]

03:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 22
	Interrupt: pin A routed to IRQ 11
	Region 1: Memory at 28000800 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at e080 [size=32]
	Capabilities: <access denied>

03:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 22
	Interrupt: pin A routed to IRQ 11
	Region 1: Memory at 28000900 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at e0a0 [size=32]
	Capabilities: <access denied>

03:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 22, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 28000a00 (32-bit, non-prefetchable) [size=256]
	Region 1: Memory at 28000b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (63750ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 28000000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at e000 [size=128]
	Capabilities: <access denied>

---

