---
title: "Broadcom NetXtreme BCM5761 not working"
date: 2014-03-12
forum: Hardware
---

### Post by ghreyes71 on 2014-03-12
The Broadcom BCM5761 network device could not to be initialized properly on boot time; therefore, the associated
interface could not obtain an IP address via DHCP or be assigned one manually. 

Testing with another SO: with Debian Wheezy Live: PASS!

Temporal Solution: when the system load is complete, if I delete the module and reload it, and then restart the network service, the NIC starts transmitting.

Background:
[https://bugzilla.redhat.com/show_bug.cgi?id=521241](https://bugzilla.redhat.com/show_bug.cgi?id=521241)
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=ar&lc=es&dlc=es&docname=c03486708](http://h10025.www1.hp.com/ewfrf/wc/document?cc=ar&lc=es&dlc=es&docname=c03486708)
[https://bugzilla.redhat.com/show_bug.cgi?id=486601](https://bugzilla.redhat.com/show_bug.cgi?id=486601)
[http://ubuntuforums.org/showthread.php?t=1342342](http://ubuntuforums.org/showthread.php?t=1342342)

Environment:
Kernel: 2.6.24-21-generic [upgrade infeasible]
NIC: Broadcom BCM5761
Driver: tg3 version: 3.133d
Firmware version: 5761-v3.79
CPU: all are Lenovo ThinkCentre M Series

Output of sudo lspci -vv:

```

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Lenovo Device 3082
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 40
	Region 0: Memory at fea10000 (64-bit, non-prefetchable) [size=64K]
	Region 2: Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [40] Vital Product Data
		Product Name: B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/\x00B&#65533;/
		Unknown small resource type 00, will not decode more.
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 4161
	Capabilities: [cc] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number ec-a8-6b-ff-fe-cb-3f-2d
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: tg3
```

Output of sudo lshw -C network:```


  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: ec:a8:6b:cb:3f:2d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=half firmware=5761-v3.79 DASH v1.46.0.0 ip=10.254.64.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:fea10000-fea1ffff memory:fea00000-fea0ffff
```

Driver version:

```
$ modinfo tg3
filename:       /lib/modules/2.6.24-21-generic/updates/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.133d
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller (davem@redhat.com) and Jeff Garzik (jgarzik@pobox.com)
srcversion:     C57DB435FA3F4000DF2B4F2

```

The previous version didnt work with the trick above indicated:

```
filename:       /lib/modules/2.6.24-21-generic/kernel/drivers/net/tg3.ko
version:        3.86
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller (davem@redhat.com) and Jeff Garzik (jgarzik@pobox.com)
srcversion:     11EFF1630D42EE942C86485
```

---

### Post by varunendra on 2014-03-14
> **ghreyes71 said:**
> ```
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 **[COLOR="#FF0000"]duplex=half[/COLOR]** firmware=5761-v3.79 DASH v1.46.0.0 ip=10.254.64.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
```

Does the duplex remain "half" when you reload the driver?

It maybe worth trying to install ethtool (sudo apt-get install ethtool), then add this line to your "/etc/rc.local" file (above the last line - "exit 0") -
```
ethtool -s eth0 speed 100 **duplex full** autoneg off
```

---

