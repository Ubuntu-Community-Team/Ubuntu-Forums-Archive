---
title: "Dell tuner card"
date: 2010-02-27
forum: Hardware
---

### Post by Bobboau on 2010-02-27
so I've got this new Dell studio 1747 and I've managed to get everything working super awesome except for the tuner card it's got. I don't want a full DVR I just want to watch TV so I'm intending to use tvtime, but it doesn't seem to be working as of now. it seems to be trying to pull from my camera and failing. when I lspci I get

0e:00.0 Multimedia controller: Philips Semiconductors Device 7231 (rev aa)

can anyone help me get this thing working?

---

### Post by Bobboau on 2010-02-28
anyone?

---

### Post by Bobboau on 2010-03-01
windows apparently calls it "AverMedia A338 Hybrid Analog/ATSC"

---

### Post by Bobboau on 2010-03-02
this topic is likely to be indexed by google and people with this problem in the future are likely to find this topic.

---

### Post by Bobboau on 2010-03-02
I'm sure someone will find this thread who can help me.
at least I'm not just saying 'bump' over and over again

```
0e:00.0 Multimedia controller: Philips Semiconductors Device 7231 (rev aa)
	Subsystem: Avermedia Technologies Inc Device 0607
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at f8400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [50] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <256ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [74] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [7c] Vendor Specific Information <?>
	Capabilities: [100] Vendor Specific Information <?>

```

---

### Post by Bobboau on 2010-03-12
so when you search for the lspci string this thread is now officially the second item that comes up in google, and #4 for 'AverMedia A338 Hybrid Analog/ATSC', just thought I'd share that.

---

### Post by coffeecat on 2010-03-12
Are you running Karmic? A default install is missing the non-free firmware for a number of devices including dvb tuners - for licensing reasons. Try installing the linux-firmware-nonfree package from Synaptic. You'll probably need to do a reboot before the device works properly.

---

### Post by Bobboau on 2010-03-13
yes, well technically I'm running mint, but there are not a lot of major differences aside from default packages.

I installed the package you suggested, but it does not seem to have effected anything.

---

### Post by Bobboau on 2010-03-14
well it looks like there is no solution because the driver isn't done yet
[http://jusst.de/hg/saa7231/summary](http://jusst.de/hg/saa7231/summary)
looks like it hasn't been worked on for the last half year :(

---

### Post by stevenwscott on 2010-05-27
Running 10.04 Lucid, just got a Dell 1749 w ATI HD 5600, same tag for the tuner under Windows, no device under Ubuntu. No luck any methods. sadness. :(

---

