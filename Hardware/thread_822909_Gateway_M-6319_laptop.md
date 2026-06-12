---
title: "Gateway M-6319 laptop"
date: 2008-06-08
forum: Hardware
---

### Post by drdanield@gmail.com on 2008-06-08
For notes regarding this laptop, please see 
[http://nohair.com/code/computers:ubuntu:gateway_m-6319](http://nohair.com/code/computers:ubuntu:gateway_m-6319)

Wireless: fixed with ndiswrapper
Microphone: does not work.

Here is the info for sound/mic.  

$ sudo lspci -vv -s 00:1b.0
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0380
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fa500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0


Adding "options snd-hda-intel model=ref" to end of /etc/modprobe.d/alsa-base as suggested on [http://ge.ubuntuforums.com/showthread.php?t=791031](http://ge.ubuntuforums.com/showthread.php?t=791031) does not fix the mic.

Please help fix the microphone -- thanx.

---

