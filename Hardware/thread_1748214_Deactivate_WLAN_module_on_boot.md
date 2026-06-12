---
title: "Deactivate WLAN module on boot"
date: 2011-05-03
forum: Hardware
---

### Post by SpinningAround on 2011-05-03
Would it be possible to boot with live cd (on usb) in such away that the WLAN driver/module isn't loaded. I have a problem where the laptop won't work on battery power without 'acpi=off', it even freeze when using 'acpi=ht'. One thing I noticed when using 'ht' was that the boot did get stuck on loading network driver or similar so I would like to see what will happen if I deactivate the WLAN module.

sudo lspci -vv output
```

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: AzureWave AR5007EG 802.11bg Wi-Fi mini PCI express card
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f89f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

---

### Post by IcarusR on 2011-05-03
Blacklist ath5k (wireless module) by adding it to /etc/modprobe.d/blacklist.conf & it should not load.

---

### Post by SpinningAround on 2011-05-03
> **IcarusR said:**
> Blacklist ath5k (wireless module) by adding it to /etc/modprobe.d/blacklist.conf & it should not load.

That would work if I have ubuntu installed, question is if I can do the same with the live cd, by adding something to the boot line, like 'acpi=off'. Or maybe I did miss understand you, but i cant find an /etc/ map on the boot/install/live cd-image

EDIT:
Installed ubuntu and blacklisted the module, it stopped ubuntu from freezing when unplugging AC-power but X crashed instead.

---

### Post by IcarusR on 2011-05-04
Could still have done it with live usb.

> but X crashed instead.

Check logs.

---

### Post by SpinningAround on 2011-05-05
> **IcarusR said:**
> Could still have done it with live usb.



Check logs.
I get these lines over and over again if I unplugg AC-power while WLAN card is blacklisted. Don't think it's related to X but to the kernel.
```
kernel: [***] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(4).
kernel: [***] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
```

I guess that the kernel don't support my card, I'm slightly confused since it looks like X is crashing but that the cause is the kernel.
```

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1402
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 90000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 7800 [size=256]
	Region 2: Memory at f88f0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at f88c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

```

---

