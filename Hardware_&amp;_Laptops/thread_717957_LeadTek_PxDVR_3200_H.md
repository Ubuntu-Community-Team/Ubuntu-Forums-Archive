---
title: "LeadTek PxDVR 3200 H"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Valentin_X on 2008-03-07
Hi,
can anyone help me to get this card running (in analog mode or both). 
i have tried to add to /etc/modules pciehp pciehp_force=1 and added  /etc/modeprobe.d/cx88xx with "options cx88xx card=4" but i can't get this thing running.
Chipset: Conexant CX23885/CX23417/Intel CE6353 &#8226; Hardware-MPEG2-Encoder &#8226; integrated FM Tuner, remote control

edit: hardy heron alpha 5 

lspci -vv
> 
03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)
	Subsystem: LeadTek Research Inc. Unknown device 6681
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at cfa00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <2us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000



dmesg

> 
[   37.091121] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   37.125012] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   38.192874] Linux agpgart interface v0.102
[   38.363431] nvidia: module license 'NVIDIA' taints kernel.
[   38.659604] cx23885 driver version 0.0.1 loaded
[   38.659928] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[   38.659933] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [AXV6] -> GSI 16 (level, low) -> IRQ 21
[   38.659937] cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   38.659938] cx23885[0]: try to pick one of the existing card configs via
[   38.659939] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   38.659939] cx23885[0]: version might help as well.
[   38.659941] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   38.659943] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   38.659944] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   38.659945] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   38.659946] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   38.659948] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   38.659954] CORE cx23885[0]: subsystem: 107d:6681, board: UNKNOWN/GENERIC [card=0,autodetected]
[   38.997440] cx23885[0]: i2c bus 0 registered
[   38.997460] cx23885[0]: i2c bus 1 registered
[   38.997478] cx23885[0]: i2c bus 2 registered
[   39.024009] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 21, latency: 0, mmio: 0xcfa00000
[   39.024014] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   39.306332] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   39.306335] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [AXV5] -> GSI 16 (level, low) -> IRQ 21



anyone got an idea? thx for any help
Valentin

---

### Post by madman8 on 2008-03-24
Hey

Any luck with getting that card working? I'm looking at buying one for a mythbuntu setup.

---

### Post by Valentin_X on 2008-04-11
Nope i am still searching for any help because this is the last thing i want to get working before i will erase windows else ubuntu is more or less useless because i have no normal tv...
but if i'll get it running this card is the best i ever had. the video is more than clear and the sound is perfect. the best u can get for ur money.

So

ANY help is really really welcome.
cheers 
Valentin_X

---

