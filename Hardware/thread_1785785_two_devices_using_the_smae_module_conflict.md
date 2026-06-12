---
title: "two devices using the smae module conflict"
date: 2011-06-18
forum: Hardware
---

### Post by luishasbon on 2011-06-18
Hello Dear Comunity.

I have 11.04, just updated; I have an Nvidia gts 450 wih hdmi audio support; also My Motherboard has an integrated soundcard "VIA VT1780 Azalia"; both of them, use the snd-hda-intel module; but by default alsa only recognize the Nvidia HDA soundcard. I Can't use the hdmi port so I need to use the other soundcard(Via Azalia); How do I configure alsa, in order to use the VIA Azalia soundcard with the snd-hda-intel module and not the nvidia HDA card?

Thanks

ADDED INFO

02:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2023
	Physical Slot: 0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 25
	Region 0: Memory at ddffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7253
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

---

