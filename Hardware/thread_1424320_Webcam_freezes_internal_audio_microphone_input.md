---
title: "Webcam freezes internal audio microphone input"
date: 2010-03-07
forum: Hardware
---

### Post by austinjl on 2010-03-07
So this is a curious issue for me. The internal microphone freezes/crashes when any webcam input is captured. I have to cold boot in order to restore the microphone to working order.

This is a HP dm3 laptop with a built-in webcam and microphone running Ubuntu Karmic Koala 9.10.

lspci:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3656
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at f2300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

lsusb:
Bus 001 Device 002: ID 04f2:b182 Chicony Electronics Co., Ltd

I have updated to the latest uvcvideo drivers and tried an external USB webcam which freezes the internal mic in the same manner. The external USB webcam micrphone functions fine with both webcams.

I have tried capturing the video from Skype, VLC, and Cheese. In each case, the internal mic freezes same as the others.

The following backport packages are installed:
linux-backports-modules-2.6.31
linux-backports-modules-alsa
linux-backports-modules-karmic

The internal mic works perfectly in multiple applications when the webcam input has not been captured.

Any ideas?

---

