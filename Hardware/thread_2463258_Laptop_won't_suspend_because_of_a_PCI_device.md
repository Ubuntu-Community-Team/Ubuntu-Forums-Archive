---
title: "Laptop won't suspend because of a PCI device"
date: 2021-06-07
forum: Hardware
---

### Post by zean-7 on 2021-06-07
I am running Ubuntu 20.04.2, and my laptop used to suspend properly everytime, since I installed Ubuntu. But, for a few days now, I realized that my laptop doesn't suspend at all. Everytime I close the lid, the lights are still ON, the fans still running and if I leave it for a few hours and come back, I find that the fans are running at almost full-speed and laptop has overheated a LOTTT and it doesn't turns ON after opening the lid sometimes!
I don't know what caused this issue, but I tried researching a bit myself and here are my findings:

```
sudo journalctl -b <previous_boot_id> -r | grep "failed to suspend async: error"
```
```
Jun 07 15:04:27 ThreadRipper kernel: PM: Device 0000:05:00.3 failed to suspend async: error -16
Jun 07 14:03:51 ThreadRipper kernel: PM: Device 0000:05:00.3 failed to suspend async: error -16
Jun 07 14:01:12 ThreadRipper kernel: PM: Device 0000:05:00.3 failed to suspend async: error -16

```

These are the three times I tried suspending it in my previous boots. The first two times it woke up after sometime, but the third time it didnt. The error points that a certain PM device with id: 05:00.3 is failing to suspend. So, I tried to check which PCI device was that:
```
sudo lspci | grep 05:00.3
```
```
05:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1
```

It's a USB controller that is at fault here. I tried:
```
sudo lspci -vv
```
```
05:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1 (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. Renoir USB 3.1
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 33
	Region 0: Memory at fc300000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [64] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 0.000W
		DevCtl:	CorrErr- NonFatalErr- FatalErr- UnsupReq-
			RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 16GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 16GT/s (ok), Width x16 (ok)
			TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, NROPrPrP-, LTR-
			 10BitTagComp+, 10BitTagReq-, OBFF Not Supported, ExtFmt+, EETLPPrefix+, MaxEETLPPrefixes 1
			 EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
			 FRS-, TPHComp-, ExtTPHComp-
			 AtomicOpsCap: 32bit- 64bit- 128bitCAS-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
			 AtomicOpsCtl: ReqEn-
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/8 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [c0] MSI-X: Enable+ Count=8 Masked-
		Vector table: BAR=0 offset=000fe000
		PBA: BAR=0 offset=000ff000
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

```

These are all the findings that I could gather, now I want to ask if my finding is accurate and how to fix this issue? What do I have to do to get my laptop to suspend gracefully as before?

---

### Post by CatKiller on 2021-06-07
> **zean-7 said:**
> These are all the findings that I could gather, now I want to ask if my finding is accurate 

Looks legit to me. It seems feasible that it's a USB device that's causing the issue rather than the controller, but the upshot is the same. 

> and how to fix this issue?

Try a newer kernel; try an older kernel. 

Optionally bisect between versions that work and versions that don't to find the commit that caused the problem for use with your bug report about the regression.

---

