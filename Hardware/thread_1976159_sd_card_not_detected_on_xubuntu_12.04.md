---
title: "sd card not detected on xubuntu 12.04"
date: 2012-05-08
forum: Hardware
---

### Post by GOwin on 2012-05-08
I was previously using Ubuntu 10.04 and now with a freshly installed xubuntu 12.04.

My MSI S270's internal card reader works fine in the previous version, but now I couldn't get it to read my sd cards.

According to lspci -vv it's an:
```
02:05.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 0221
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

```
I checked dmesg and /var/log/syslog but found no errors.

---

