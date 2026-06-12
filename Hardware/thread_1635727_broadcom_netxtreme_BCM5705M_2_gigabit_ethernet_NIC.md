---
title: "broadcom netxtreme BCM5705M_2 gigabit ethernet NIC on Ubuntu 9.10"
date: 2010-12-02
forum: Hardware
---

### Post by sdkumar00 on 2010-12-02
Hi All,
The netxtreme eired card on my Dell laptop is not working. The interface is showing up on ifconfig, but dmesg shows the following:
 
[ 27.964656] tg3 0000:03:00.0: firmware: requesting tigon/tg3_tso5.bin
[ 28.027724] tg3 0000:03:00.0: PME# disabled
[ 28.334294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 38.400010] eth1: no IPv6 routers present
[ 89.528013] Marking TSC unstable due to cpufreq changes
[ 89.672022] Clocksource tsc unstable (delta = -89970642 ns)
[ 225.832436] tg3 0000:03:00.0: PME# enabled
[ 225.960972] tg3 0000:03:00.0: PME# disabled
[ 226.296855] ADDRCONF(NETDEV_UP): eth0: link is not ready
 
 
Other relevant logs are below.
 
lshw -C network
 
*-network:0
description: Ethernet interface
product: NetXtreme BCM5705M_2 Gigabit Ethernet
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 03
serial: 00:12:3f:d1:ca:e5
capacity: 1GB/s
width: 64 bits
clock: 66MHz
capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5705-v3.16 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
resources: irq:9 memory:dcff0000-dcffffff
*-network:1
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:03:03.0
logical name: eth1
version: 05
serial: 00:12:f0:aa:b1:07
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
resources: irq:10 memory:dcfef000-dcfeffff
 
 
lspci -v
 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
Subsystem: Dell Device 01aa
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
Latency: 0
Capabilities: [e0] Vendor Specific Information <?>
Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000f000-00000fff
Memory behind bridge: dd000000-dfefffff
Prefetchable memory behind bridge: c0000000-cfffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: [88] Subsystem: Intel Corporation Device 0000
Capabilities: [80] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0100c Data: 4149
Capabilities: [a0] Express (v1) Root Port (Slot+), MSI 00
DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
ExtTag- RBE- FLReset-
DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
MaxPayload 128 bytes, MaxReadReq 128 bytes
DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
LnkCap: Port #2, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
ClockPM- Suprise- LLActRep- BwNot-
LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
Slot # 1, PowerLimit 75.000000; Interlock- NoCompl-
SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
Control: AttnInd Off, PwrInd On, Power- Interlock-
SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
Changed: MRL- PresDet+ LinkState-
RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
RootCap: CRSVisible-
RootSta: PME ReqID 0000, PMEStatus- PMEPending-
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 11
Region 4: I/O ports at bf80 [size=32]
Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 10
Region 4: I/O ports at bf60 [size=32]
Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin C routed to IRQ 9
Region 4: I/O ports at bf40 [size=32]
Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin D routed to IRQ 7
Region 4: I/O ports at bf20 [size=32]
Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
Subsystem: Dell Device 01aa
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 11
Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [58] Debug port: BAR=1 offset=00a0
Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
I/O behind bridge: 00002000-00002fff
Memory behind bridge: dcf00000-dcffffff
Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: [50] Subsystem: Dell Device 01aa
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 11
Region 0: I/O ports at ed00 [size=256]
Region 1: I/O ports at ec40 [size=64]
Region 2: Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
Region 3: Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Kernel driver in use: Intel ICH
Kernel modules: snd-intel8x0
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 10
Region 0: I/O ports at 01f0 [size=8]
Region 1: I/O ports at 03f4 [size=1]
Region 2: I/O ports at 0170 [size=8]
Region 3: I/O ports at 0374 [size=1]
Region 4: I/O ports at bfa0 [size=16]
Capabilities: [70] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
Subsystem: Dell Device 01aa
Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Interrupt: pin B routed to IRQ 10
Region 4: I/O ports at 10c0 [size=32]
Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation NV41.9 [GeForce Go 6800 Ultra] (rev a2)
Subsystem: Dell Device 019c
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 11
Region 0: Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
Region 3: Memory at de000000 (64-bit, non-prefetchable) [size=16M]
Expansion ROM at dfe00000 [disabled] [size=128K]
Capabilities: [60] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Address: 0000000000000000 Data: 0000
Capabilities: [78] Express (v1) Endpoint, MSI 00
DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
MaxPayload 128 bytes, MaxReadReq 512 bytes
DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
LnkCap: Port #0, Speed 2.5GT/s, Width x16, ASPM L0s, Latency L0 <256ns, L1 <16us
ClockPM- Suprise- LLActRep- BwNot-
LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
Kernel modules: nvidiafb
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
Subsystem: Dell Device 01aa
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (16000ns min), Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 9
Region 0: Memory at dcff0000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: [48] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=1 PME-
Capabilities: [50] Vital Product Data <?>
Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
Address: 3775edffff7ffffc Data: 7eff
Kernel driver in use: tg3
Kernel modules: tg3
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
Subsystem: Dell Device 01aa
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 168
Interrupt: pin A routed to IRQ 7
Region 0: Memory at dcf00000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
Memory window 0: 30000000-33fff000 (prefetchable)
Memory window 1: 34000000-37fff000
I/O window 0: 00002000-000020ff
I/O window 1: 00002400-000024ff
BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10)
Subsystem: Dell Device 01aa
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (500ns min, 1000ns max)
Interrupt: pin B routed to IRQ 9
Region 0: Memory at dcfee800 (32-bit, non-prefetchable) [size=2K]
Capabilities: [dc] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=2 PME+
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
Subsystem: Dell Device 01aa
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64
Interrupt: pin C routed to IRQ 10
Region 0: Memory at dcfee700 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=2 PME-
Kernel driver in use: sdhci-pci
Kernel modules: sdhci-pci
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
Subsystem: Intel Corporation Device 2721
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (750ns min, 6000ns max), Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 10
Region 0: Memory at dcfef000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [dc] Power Management version 2
Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=1 PME-
Kernel driver in use: ipw2200
Kernel modules: ipw2200
 
ifconfig
 
eth0 Link encap:Ethernet HWaddr 00:12:3f:d1:ca:e5 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 
eth1 Link encap:Ethernet HWaddr 00:12:f0:aa:b1:07 
inet6 addr: fe80::212:f0ff:feaa:b107/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:10 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:156 (156.0 B)
Interrupt:10 Base address:0x6000 Memory:dcfef000-dcfeffff 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
 
dmesg
 
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.31-20-386 (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 07:29:24 UTC 2010 (Ubuntu 2.6.31-20.58-386)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[ 0.000000] BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000002ffda000 (usable)
[ 0.000000] BIOS-e820: 000000002ffda000 - 0000000030000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[ 0.000000] BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] DMI 2.3 present.
[ 0.000000] last_pfn = 0x2ffda max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-CFFFF write-protect
[ 0.000000] D0000-EFFFF uncachable
[ 0.000000] F0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask FE0000000 write-back
[ 0.000000] 1 base 020000000 mask FF0000000 write-back
[ 0.000000] 2 base 0FEDA0000 mask FFFFE0000 write-through
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] PAT not supported by CPU.
[ 0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[ 0.000000] Scanning 1 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000002000 (usable)
[ 0.000000] modified: 0000000000002000 - 0000000000006000 (reserved)
[ 0.000000] modified: 0000000000006000 - 000000000009f000 (usable)
[ 0.000000] modified: 000000000009f000 - 00000000000a0000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000002ffda000 (usable)
[ 0.000000] modified: 000000002ffda000 - 0000000030000000 (reserved)
[ 0.000000] modified: 00000000e0000000 - 00000000f0007000 (reserved)
[ 0.000000] modified: 00000000f0008000 - 00000000f000c000 (reserved)
[ 0.000000] modified: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] modified: 00000000fed20000 - 00000000fee10000 (reserved)
[ 0.000000] modified: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 00c00000
[ 0.000000] init_memory_mapping: 0000000000000000-000000002ffda000
[ 0.000000] Using x86 segment limits to approximate NX protection
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 002fc00000 page 2M
[ 0.000000] 002fc00000 - 002ffda000 page 4k
[ 0.000000] kernel direct mapping tables up to 2ffda000 @ 7000-c000
[ 0.000000] RAMDISK: 238d8000 - 24022f69
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 767MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 2ffda000
[ 0.000000] low ram: 0 - 2ffda000
[ 0.000000] node 0 low ram: 00000000 - 2ffda000
[ 0.000000] node 0 bootmap 00008000 - 0000dffc
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 002ffda000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008933c0] TEXT DATA BSS ==> [0000100000 - 00008933c0]
[ 0.000000] #4 [00238d8000 - 0024022f69] RAMDISK ==> [00238d8000 - 0024022f69]
[ 0.000000] #5 [000009f000 - 0000100000] BIOS reserved ==> [000009f000 - 0000100000]
[ 0.000000] #6 [0000894000 - 0000897188] BRK ==> [0000894000 - 0000897188]
[ 0.000000] #7 [0000007000 - 0000008000] PGTABLE ==> [0000007000 - 0000008000]
[ 0.000000] #8 [0000008000 - 000000e000] BOOTMAP ==> [0000008000 - 000000e000]
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x0002ffda
[ 0.000000] HighMem 0x0002ffda -> 0x0002ffda
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[3] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x00000002
[ 0.000000] 0: 0x00000006 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0002ffda
[ 0.000000] On node 0 totalpages: 196469
[ 0.000000] free_area_init_node: node 0, pgdat c0776460, node_mem_map c1000000
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3963 pages, LIFO batch:0
[ 0.000000] Normal zone: 1504 pages used for memmap
[ 0.000000] Normal zone: 190970 pages, LIFO batch:31
[ 0.000000] Using APIC driver default
[ 0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[ 0.000000] Found and enabled local APIC!
[ 0.000000] nr_irqs_gsi: 16
[ 0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:b0000000)
[ 0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 13 pages at c1604000, static data 30460 bytes
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 194933
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-386 root=UUID=08853dfb-6dea-41fd-b5cc-9511a6737177 ro quiet splash acpi=off irqpoll
[ 0.000000] Misrouted IRQ fixup and polling support enabled
[ 0.000000] This may significantly impact system performance
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 3931400 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (00000000:00000000)
[ 0.000000] Memory: 759400k/786280k available (4522k kernel code, 26116k reserved, 2128k data, 536k init, 0k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff1d000 - 0xfffff000 ( 904 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xf07da000 - 0xff7fe000 ( 240 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xeffda000 ( 767 MB)
[ 0.000000] .init : 0xc077f000 - 0xc0805000 ( 536 kB)
[ 0.000000] .data : 0xc056a9f8 - 0xc077eb28 (2128 kB)
[ 0.000000] .text : 0xc0100000 - 0xc056a9f8 (4522 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.000000] NR_IRQS:2304 nr_irqs:256
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1994.966 MHz processor.
[ 0.002060] Console: colour VGA+ 80x25
[ 0.002064] console [tty0] enabled
[ 0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.93 BogoMIPS (lpj=7979864)
[ 0.004031] Security Framework initialized
[ 0.004054] AppArmor: AppArmor initialized
[ 0.004061] Mount-cache hash table entries: 512
[ 0.004183] Initializing cgroup subsys ns
[ 0.004188] Initializing cgroup subsys cpuacct
[ 0.004192] Initializing cgroup subsys memory
[ 0.004199] Initializing cgroup subsys freezer
[ 0.004201] Initializing cgroup subsys net_cls
[ 0.004216] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 0.004219] CPU: L2 cache: 2048K
[ 0.004224] mce: CPU supports 5 MCE banks
[ 0.004231] CPU0: Thermal monitoring enabled (TM1)
[ 0.004241] Checking 'hlt' instruction... OK.
[ 0.020742] SMP alternatives: switching to UP code
[ 0.026640] Freeing SMP alternatives: 19k freed
[ 0.026693] weird, boot CPU (#0) not listed by the BIOS.
[ 0.026695] SMP motherboard not detected.
[ 0.132016] SMP disabled
[ 0.132114] Brought up 1 CPUs
[ 0.132117] Total of 1 processors activated (3989.93 BogoMIPS).
[ 0.132127] CPU0 attaching NULL sched-domain.
[ 0.132312] Booting paravirtualized kernel on bare hardware
[ 0.132498] regulator: core version 0.5
[ 0.132526] Time: 11:48:02 Date: 12/02/10
[ 0.132570] NET: Registered protocol family 16
[ 0.132689] EISA bus registered
[ 0.170413] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=10
[ 0.170415] PCI: Using configuration type 1 for base access
[ 0.171391] bio: create slab <bio-0> at 0
[ 0.171438] ACPI: Interpreter disabled.
[ 0.171560] SCSI subsystem initialized
[ 0.171591] libata version 3.00 loaded.
[ 0.171653] usbcore: registered new interface driver usbfs
[ 0.171665] usbcore: registered new interface driver hub
[ 0.171687] usbcore: registered new device driver usb
[ 0.171783] PCI: Probing PCI hardware
[ 0.171786] PCI: Probing PCI hardware (bus 00)
[ 0.171876] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.171880] pci 0000:00:01.0: PME# disabled
[ 0.171964] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[ 0.172030] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[ 0.172091] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[ 0.172151] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[ 0.172216] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[ 0.172276] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.172281] pci 0000:00:1d.7: PME# disabled
[ 0.172382] pci 0000:00:1e.2: reg 10 io port: [0xed00-0xedff]
[ 0.172390] pci 0000:00:1e.2: reg 14 io port: [0xec40-0xec7f]
[ 0.172398] pci 0000:00:1e.2: reg 18 32bit mmio: [0xdffffe00-0xdfffffff]
[ 0.172406] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xdffffd00-0xdffffdff]
[ 0.172443] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[ 0.172448] pci 0000:00:1e.2: PME# disabled
[ 0.172538] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[ 0.172546] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[ 0.172550] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[ 0.172555] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[ 0.172597] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[ 0.172605] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[ 0.172613] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[ 0.172621] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[ 0.172629] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[ 0.172662] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.172667] pci 0000:00:1f.2: PME# disabled
[ 0.172727] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[ 0.172783] pci 0000:01:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[ 0.172792] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[ 0.172801] pci 0000:01:00.0: reg 1c 64bit mmio: [0xde000000-0xdeffffff]
[ 0.172810] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe1ffff]
[ 0.172877] pci 0000:00:01.0: bridge 32bit mmio: [0xdd000000-0xdfefffff]
[ 0.172881] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc0000000-0xcfffffff]
[ 0.172957] pci 0000:03:00.0: reg 10 64bit mmio: [0xdcff0000-0xdcffffff]
[ 0.173035] pci 0000:03:00.0: PME# supported from D3hot D3cold
[ 0.173041] pci 0000:03:00.0: PME# disabled
[ 0.173089] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[ 0.173113] pci 0000:03:01.0: supports D1 D2
[ 0.173115] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.173120] pci 0000:03:01.0: PME# disabled
[ 0.173163] pci 0000:03:01.1: reg 10 32bit mmio: [0xdcfee800-0xdcfeefff]
[ 0.173220] pci 0000:03:01.1: supports D1 D2
[ 0.173223] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.173228] pci 0000:03:01.1: PME# disabled
[ 0.173270] pci 0000:03:01.2: reg 10 32bit mmio: [0xdcfee700-0xdcfee7ff]
[ 0.173329] pci 0000:03:01.2: supports D1 D2
[ 0.173331] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.173337] pci 0000:03:01.2: PME# disabled
[ 0.173394] pci 0000:03:03.0: reg 10 32bit mmio: [0xdcfef000-0xdcfeffff]
[ 0.173461] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[ 0.173466] pci 0000:03:03.0: PME# disabled
[ 0.173523] pci 0000:00:1e.0: transparent bridge
[ 0.173530] pci 0000:00:1e.0: bridge 32bit mmio: [0xdcf00000-0xdcffffff]
[ 0.174226] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:2641]
[ 0.174403] Bluetooth: Core ver 2.15
[ 0.174426] NET: Registered protocol family 31
[ 0.174428] Bluetooth: HCI device and connection manager initialized
[ 0.174431] Bluetooth: HCI socket layer initialized
[ 0.174433] NetLabel: Initializing
[ 0.174435] NetLabel: domain hash size = 128
[ 0.174437] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.174451] NetLabel: unlabeled traffic allowed by default
[ 0.174587] hpet clockevent registered
[ 0.174591] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.174598] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.174603] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.181599] pnp: PnP ACPI: disabled
[ 0.181604] PnPBIOS: Scanning system for PnP BIOS support...
[ 0.181641] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
[ 0.181644] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
[ 0.181735] pnp 00:01: io resource (0x1000-0x105f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[ 0.181739] pnp 00:01: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[ 0.181986] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[ 0.181997] system 00:01: ioport range 0x1080-0x10bf has been reserved
[ 0.182000] system 00:01: ioport range 0x10c0-0x10ff could not be reserved
[ 0.182003] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[ 0.182006] system 00:01: ioport range 0x900-0x97f has been reserved
[ 0.182010] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[ 0.182013] system 00:01: iomem range 0x100000-0x2fffffff could not be reserved
[ 0.182016] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[ 0.182020] system 00:01: iomem range 0xffb80000-0xffbfffff has been reserved
[ 0.182023] system 00:01: iomem range 0xfff80000-0xffffffff has been reserved
[ 0.182026] system 00:01: iomem range 0xfeda0000-0xfedfffff has been reserved
[ 0.182032] system 00:04: iomem range 0xf0000000-0xf000bfff could not be reserved
[ 0.182037] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[ 0.182182] AppArmor: AppArmor Filesystem Enabled
[ 0.182213] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.182215] pci 0000:00:01.0: IO window: disabled
[ 0.182220] pci 0000:00:01.0: MEM window: 0xdd000000-0xdfefffff
[ 0.182223] pci 0000:00:01.0: PREFETCH window: 0xc0000000-0xcfffffff
[ 0.182233] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[ 0.182236] pci 0000:03:01.0: IO window: 0x002000-0x0020ff
[ 0.182241] pci 0000:03:01.0: IO window: 0x002400-0x0024ff
[ 0.182246] pci 0000:03:01.0: PREFETCH window: 0x30000000-0x33ffffff
[ 0.182252] pci 0000:03:01.0: MEM window: 0x34000000-0x37ffffff
[ 0.182257] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[ 0.182261] pci 0000:00:1e.0: IO window: 0x2000-0x2fff
[ 0.182267] pci 0000:00:1e.0: MEM window: 0xdcf00000-0xdcffffff
[ 0.182272] pci 0000:00:1e.0: PREFETCH window: 0x30000000-0x33ffffff
[ 0.182284] pci 0000:00:01.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[ 0.182289] pci 0000:00:01.0: setting latency timer to 64
[ 0.182298] pci 0000:00:1e.0: setting latency timer to 64
[ 0.182311] PCI: setting IRQ 7 as level-triggered
[ 0.182315] pci 0000:03:01.0: found PCI INT A -> IRQ 7
[ 0.182326] pci 0000:03:01.0: sharing IRQ 7 with 0000:00:1d.3
[ 0.182355] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 0.182359] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[ 0.182362] pci_bus 0000:01: resource 1 mem: [0xdd000000-0xdfefffff]
[ 0.182365] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[ 0.182368] pci_bus 0000:03: resource 0 io: [0x2000-0x2fff]
[ 0.182371] pci_bus 0000:03: resource 1 mem: [0xdcf00000-0xdcffffff]
[ 0.182374] pci_bus 0000:03: resource 2 pref mem [0x30000000-0x33ffffff]
[ 0.182377] pci_bus 0000:03: resource 3 io: [0x00-0xffff]
[ 0.182379] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[ 0.182382] pci_bus 0000:04: resource 0 io: [0x2000-0x20ff]
[ 0.182385] pci_bus 0000:04: resource 1 io: [0x2400-0x24ff]
[ 0.182388] pci_bus 0000:04: resource 2 pref mem [0x30000000-0x33ffffff]
[ 0.182391] pci_bus 0000:04: resource 3 mem: [0x34000000-0x37ffffff]
[ 0.182421] NET: Registered protocol family 2
[ 0.182510] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.182802] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.183713] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.184371] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.184375] TCP reno registered
[ 0.184502] NET: Registered protocol family 1
[ 0.184574] Trying to unpack rootfs image as initramfs...
[ 0.394884] Freeing initrd memory: 7467k freed
[ 0.401666] cpufreq-nforce2: No nForce2 chipset.
[ 0.401693] Scanning for low memory corruption every 60 seconds
[ 0.401819] audit: initializing netlink socket (disabled)
[ 0.401853] type=2000 audit(1291290482.400:1): initialized
[ 0.410554] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.411958] VFS: Disk quotas dquot_6.5.2
[ 0.412014] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.412561] fuse init (API version 7.12)
[ 0.412648] msgmni has been set to 1498
[ 0.412843] alg: No test for stdrng (krng)
[ 0.412855] io scheduler noop registered
[ 0.412857] io scheduler anticipatory registered
[ 0.412859] io scheduler deadline registered (default)
[ 0.412899] io scheduler cfq registered
[ 0.428052] pci 0000:01:00.0: Boot video device
[ 0.428125] pcieport-driver 0000:00:01.0: device [8086:2591] has invalid IRQ; check vendor BIOS
[ 0.428159] alloc irq_desc for 16 on node -1
[ 0.428161] alloc kstat_irqs on node -1
[ 0.428171] pcieport-driver 0000:00:01.0: irq 16 for MSI/MSI-X
[ 0.428177] pcieport-driver 0000:00:01.0: setting latency timer to 64
[ 0.428234] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.428259] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.428329] isapnp: Scanning for PnP cards...
[ 0.676069] Switched to high resolution mode on CPU 0
[ 0.782005] isapnp: No Plug & Play device found
[ 0.783019] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.784290] brd: module loaded
[ 0.784727] loop: module loaded
[ 0.784803] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 0.784882] ahci 0000:00:1f.2: version 3.0
[ 0.784897] PCI: setting IRQ 10 as level-triggered
[ 0.784901] ahci 0000:00:1f.2: found PCI INT B -> IRQ 10
[ 0.784909] ahci 0000:00:1f.2: sharing IRQ 10 with 0000:00:1d.1
[ 0.784927] ahci 0000:00:1f.2: sharing IRQ 10 with 0000:00:1f.3
[ 0.784938] ahci 0000:00:1f.2: sharing IRQ 10 with 0000:03:01.2
[ 0.784943] ahci 0000:00:1f.2: sharing IRQ 10 with 0000:03:03.0
[ 0.784955] ahci: probe of 0000:00:1f.2 failed with error -22
[ 0.784993] ata_piix 0000:00:1f.2: version 2.13
[ 0.785003] ata_piix 0000:00:1f.2: found PCI INT B -> IRQ 10
[ 0.785010] ata_piix 0000:00:1f.2: sharing IRQ 10 with 0000:00:1d.1
[ 0.785027] ata_piix 0000:00:1f.2: sharing IRQ 10 with 0000:00:1f.3
[ 0.785038] ata_piix 0000:00:1f.2: sharing IRQ 10 with 0000:03:01.2
[ 0.785043] ata_piix 0000:00:1f.2: sharing IRQ 10 with 0000:03:03.0
[ 0.785049] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[ 0.940025] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 0.940099] scsi0 : ata_piix
[ 0.940169] scsi1 : ata_piix
[ 0.940203] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[ 0.940206] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[ 0.940998] Fixed MDIO Bus: probed
[ 0.941032] PPP generic driver version 2.4.2
[ 0.941106] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.941125] PCI: setting IRQ 11 as level-triggered
[ 0.941129] ehci_hcd 0000:00:1d.7: found PCI INT A -> IRQ 11
[ 0.941135] ehci_hcd 0000:00:1d.7: sharing IRQ 11 with 0000:00:1d.0
[ 0.941148] ehci_hcd 0000:00:1d.7: sharing IRQ 11 with 0000:00:1e.2
[ 0.941157] ehci_hcd 0000:00:1d.7: sharing IRQ 11 with 0000:01:00.0
[ 0.941178] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 0.941182] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 0.941209] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 0.945113] ehci_hcd 0000:00:1d.7: debug port 1
[ 0.945120] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 0.945354] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xffa80800
[ 0.960009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 0.960104] usb usb1: configuration #1 chosen from 1 choice
[ 0.960132] hub 1-0:1.0: USB hub found
[ 0.960141] hub 1-0:1.0: 8 ports detected
[ 0.960206] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.960223] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.960245] uhci_hcd 0000:00:1d.0: found PCI INT A -> IRQ 11
[ 0.960258] uhci_hcd 0000:00:1d.0: sharing IRQ 11 with 0000:00:1d.7
[ 0.960264] uhci_hcd 0000:00:1d.0: sharing IRQ 11 with 0000:00:1e.2
[ 0.960273] uhci_hcd 0000:00:1d.0: sharing IRQ 11 with 0000:01:00.0
[ 0.960289] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 0.960293] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 0.960321] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 0.960346] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[ 0.960421] usb usb2: configuration #1 chosen from 1 choice
[ 0.960445] hub 2-0:1.0: USB hub found
[ 0.960452] hub 2-0:1.0: 2 ports detected
[ 0.960494] uhci_hcd 0000:00:1d.1: found PCI INT B -> IRQ 10
[ 0.960514] uhci_hcd 0000:00:1d.1: sharing IRQ 10 with 0000:00:1f.2
[ 0.960518] uhci_hcd 0000:00:1d.1: sharing IRQ 10 with 0000:00:1f.3
[ 0.960529] uhci_hcd 0000:00:1d.1: sharing IRQ 10 with 0000:03:01.2
[ 0.960534] uhci_hcd 0000:00:1d.1: sharing IRQ 10 with 0000:03:03.0
[ 0.960540] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 0.960543] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 0.960581] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 0.960608] uhci_hcd 0000:00:1d.1: irq 10, io base 0x0000bf60
[ 0.960681] usb usb3: configuration #1 chosen from 1 choice
[ 0.960705] hub 3-0:1.0: USB hub found
[ 0.960717] hub 3-0:1.0: 2 ports detected
[ 0.960759] PCI: setting IRQ 9 as level-triggered
[ 0.960763] uhci_hcd 0000:00:1d.2: found PCI INT C -> IRQ 9
[ 0.960788] uhci_hcd 0000:00:1d.2: sharing IRQ 9 with 0000:03:00.0
[ 0.960795] uhci_hcd 0000:00:1d.2: sharing IRQ 9 with 0000:03:01.1
[ 0.960805] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 0.960808] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 0.960833] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 0.960858] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000bf40
[ 0.960929] usb usb4: configuration #1 chosen from 1 choice
[ 0.960952] hub 4-0:1.0: USB hub found
[ 0.960958] hub 4-0:1.0: 2 ports detected
[ 0.961001] uhci_hcd 0000:00:1d.3: found PCI INT D -> IRQ 7
[ 0.961028] uhci_hcd 0000:00:1d.3: sharing IRQ 7 with 0000:03:01.0
[ 0.961041] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 0.961044] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 0.961069] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 0.961094] uhci_hcd 0000:00:1d.3: irq 7, io base 0x0000bf20
[ 0.961165] usb usb5: configuration #1 chosen from 1 choice
[ 0.961189] hub 5-0:1.0: USB hub found
[ 0.961195] hub 5-0:1.0: 2 ports detected
[ 0.961290] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 0.969386] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.969392] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.969440] mice: PS/2 mouse device common for all mice
[ 0.969517] rtc_cmos 00:0b: rtc core: registered rtc_cmos as rtc0
[ 0.969545] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[ 0.969639] device-mapper: uevent: version 1.0.3
[ 0.970216] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 0.970283] device-mapper: multipath: version 1.1.0 loaded
[ 0.970286] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.970397] EISA: Probing bus 0 at eisa.0
[ 0.970403] Cannot allocate resource for EISA slot 1
[ 0.970405] Cannot allocate resource for EISA slot 2
[ 0.970428] EISA: Detected 0 cards.
[ 0.970467] cpuidle: using governor ladder
[ 0.970469] cpuidle: using governor menu
[ 0.970929] TCP cubic registered
[ 0.971081] NET: Registered protocol family 10
[ 0.971480] lo: Disabled Privacy Extensions
[ 0.971762] NET: Registered protocol family 17
[ 0.971777] Bluetooth: L2CAP ver 2.13
[ 0.971779] Bluetooth: L2CAP socket layer initialized
[ 0.971782] Bluetooth: SCO (Voice Link) ver 0.6
[ 0.971783] Bluetooth: SCO socket layer initialized
[ 0.971811] Bluetooth: RFCOMM TTY layer initialized
[ 0.971814] Bluetooth: RFCOMM socket layer initialized
[ 0.971815] Bluetooth: RFCOMM ver 1.11
[ 0.971861] Using IPI No-Shortcut mode
[ 0.971923] PM: Resume from disk failed.
[ 0.971935] registered taskstats version 1
[ 0.972033] Magic number: 6:140:832
[ 0.972091] rtc_cmos 00:0b: setting system clock to 2010-12-02 11:48:03 UTC (1291290483)
[ 0.972095] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.972097] EDD information not available.
[ 0.973808] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 1.108617] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS6, max UDMA/33
[ 1.109079] ata1.00: ATA-6: Hitachi HTS541060G9AT00, MB3OA61A, max UDMA/100
[ 1.109083] ata1.00: 117210240 sectors, multi 8: LBA48 
[ 1.109097] ata1.00: applying bridge limits
[ 1.124517] ata2.00: configured for UDMA/33
[ 1.124902] ata1.00: configured for UDMA/100
[ 1.125013] scsi 0:0:0:0: Direct-Access ATA Hitachi HTS54106 MB3O PQ: 0 ANSI: 5
[ 1.125120] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.125157] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[ 1.125200] sd 0:0:0:0: [sda] Write Protect is off
[ 1.125203] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.125225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.125342] sda:
[ 1.126063] scsi 1:0:0:0: CD-ROM SONY DVD+-RW DW-D56A PDS6 PQ: 0 ANSI: 5
[ 1.129012] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 1.129016] Uniform CD-ROM driver Revision: 3.20
[ 1.129082] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.129120] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1.141208] sda1 sda2 < sda5 >
[ 1.161171] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.161186] Freeing unused kernel memory: 536k freed
[ 1.161485] Write protecting the kernel text: 4524k
[ 1.161521] Write protecting the kernel read-only data: 1824k
[ 1.280580] Linux agpgart interface v0.103
[ 1.350820] tg3.c:v3.99 (April 20, 2009)
[ 1.350843] tg3 0000:03:00.0: found PCI INT A -> IRQ 9
[ 1.350854] tg3 0000:03:00.0: sharing IRQ 9 with 0000:00:1d.2
[ 1.350877] tg3 0000:03:00.0: sharing IRQ 9 with 0000:03:01.1
[ 1.362246] tg3 0000:03:00.0: PME# disabled
[ 1.418893] eth0: Tigon3 [partno(BCM95705A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:12:3f:d1:ca:e5
[ 1.418898] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0])
[ 1.418901] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[ 1.418904] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[ 1.419262] ohci1394 0000:03:01.1: found PCI INT B -> IRQ 9
[ 1.419274] ohci1394 0000:03:01.1: sharing IRQ 9 with 0000:00:1d.2
[ 1.419292] ohci1394 0000:03:01.1: sharing IRQ 9 with 0000:03:00.0
[ 1.478022] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9] MMIO=[dcfee800-dcfeefff] Max Packet=[2048] IR/IT contexts=[4/4]
[ 1.609741] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 1.818527] usb 2-1: configuration #1 chosen from 1 choice
[ 1.833880] usbcore: registered new interface driver hiddev
[ 1.856357] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[ 1.856437] generic-usb 0003:046D:C019.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[ 1.856464] usbcore: registered new interface driver usbhid
[ 1.856467] usbhid: v2.6:USB HID core driver
[ 2.092008] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 2.278826] usb 3-1: configuration #1 chosen from 1 choice
[ 2.549405] PM: Starting manual resume from disk
[ 2.549410] PM: Resume from partition 8:5
[ 2.549412] PM: Checking hibernation image.
[ 2.549561] PM: Resume from disk failed.
[ 2.573828] EXT4-fs (sda1): barriers enabled
[ 2.590946] kjournald2 starting: pid 333, dev sda1:8, commit interval 5 seconds
[ 2.590971] EXT4-fs (sda1): delayed allocation enabled
[ 2.590975] EXT4-fs: file extents enabled
[ 2.592882] EXT4-fs: mballoc enabled
[ 2.592899] EXT4-fs (sda1): mounted filesystem with ordered data mode
[ 2.760133] ieee1394: Host added: ID:BUS[0-00:1023] GUID[324fc0003cbd68e1]
[ 3.382812] type=1505 audit(1291290485.909:2): operation="profile_load" pid=357 name=/usr/share/gdm/guest-session/Xsession
[ 3.385363] type=1505 audit(1291290485.911:3): operation="profile_load" pid=358 name=/sbin/dhclient3
[ 3.385993] type=1505 audit(1291290485.911:4): operation="profile_load" pid=358 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 3.386338] type=1505 audit(1291290485.911:5): operation="profile_load" pid=358 name=/usr/lib/connman/scripts/dhclient-script
[ 3.444473] type=1505 audit(1291290485.971:6): operation="profile_load" pid=359 name=/usr/bin/evince
[ 3.454368] type=1505 audit(1291290485.979:7): operation="profile_load" pid=359 name=/usr/bin/evince-previewer
[ 3.460227] type=1505 audit(1291290485.987:8): operation="profile_load" pid=359 name=/usr/bin/evince-thumbnailer
[ 3.473848] type=1505 audit(1291290485.999:9): operation="profile_load" pid=361 name=/usr/lib/cups/backend/cups-pdf
[ 3.474593] type=1505 audit(1291290485.999:10): operation="profile_load" pid=361 name=/usr/sbin/cupsd
[ 5.819842] Adding 2249060k swap on /dev/sda5. Priority:-1 extents:1 across:2249060k 
[ 9.064008] EXT4-fs (sda1): internal journal on sda1:8
[ 10.936150] udev: starting version 147
[ 12.605580] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[ 12.826688] Bluetooth: Generic Bluetooth USB driver ver 0.5
[ 12.826792] usbcore: registered new interface driver btusb
[ 12.924199] dell-wmi: No known WMI GUID found
[ 13.189271] lp: driver loaded but no devices found
[ 13.384391] intel_rng: FWH not detected
[ 13.491024] lib80211: common routines for IEEE802.11 drivers
[ 13.491028] lib80211_crypt: registered algorithm 'NULL'
[ 13.630356] sdhci: Secure Digital Host Controller Interface driver
[ 13.630360] sdhci: Copyright(c) Pierre Ossman
[ 13.643451] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input3
[ 13.663663] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input4
[ 13.867179] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[ 13.867201] sdhci-pci 0000:03:01.2: found PCI INT C -> IRQ 10
[ 13.867211] sdhci-pci 0000:03:01.2: sharing IRQ 10 with 0000:00:1d.1
[ 13.867226] sdhci-pci 0000:03:01.2: sharing IRQ 10 with 0000:00:1f.2
[ 13.867230] sdhci-pci 0000:03:01.2: sharing IRQ 10 with 0000:00:1f.3
[ 13.867244] sdhci-pci 0000:03:01.2: sharing IRQ 10 with 0000:03:03.0
[ 13.869332] Registered led device: mmc0::
[ 13.870362] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[ 14.031559] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 14.461913] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 14.461916] ieee80211: Copyright (C) 2004-2005 Intel Corporation <[EMAIL="jketreno@linux.intel.com"]jketreno@linux.intel.com[/EMAIL]>
[ 14.616689] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01aa]
[ 14.729291] __ratelimit: 3 callbacks suppressed
[ 14.729294] type=1505 audit(1291290497.255:12): operation="profile_replace" pid=654 name=/usr/share/gdm/guest-session/Xsession
[ 14.730700] type=1505 audit(1291290497.255:13): operation="profile_replace" pid=655 name=/sbin/dhclient3
[ 14.731334] type=1505 audit(1291290497.255:14): operation="profile_replace" pid=655 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 14.731682] type=1505 audit(1291290497.255:15): operation="profile_replace" pid=655 name=/usr/lib/connman/scripts/dhclient-script
[ 14.735726] type=1505 audit(1291290497.259:16): operation="profile_replace" pid=656 name=/usr/bin/evince
[ 14.744463] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0038, PCI irq 7
[ 14.744467] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[ 14.744472] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[ 14.744483] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[ 14.744487] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[ 14.744671] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xdcf00000 - 0xdcffffff
[ 14.744674] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[ 14.747935] type=1505 audit(1291290497.271:17): operation="profile_replace" pid=656 name=/usr/bin/evince-previewer
[ 14.754171] type=1505 audit(1291290497.279:18): operation="profile_replace" pid=656 name=/usr/bin/evince-thumbnailer
[ 14.762499] type=1505 audit(1291290497.287:19): operation="profile_replace" pid=659 name=/usr/lib/cups/backend/cups-pdf
[ 14.763247] type=1505 audit(1291290497.287:20): operation="profile_replace" pid=659 name=/usr/sbin/cupsd
[ 14.765321] type=1505 audit(1291290497.291:21): operation="profile_replace" pid=660 name=/usr/sbin/tcpdump
[ 15.269774] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 15.269778] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 15.269858] ipw2200 0000:03:03.0: found PCI INT A -> IRQ 10
[ 15.269868] ipw2200 0000:03:03.0: sharing IRQ 10 with 0000:00:1d.1
[ 15.269883] ipw2200 0000:03:03.0: sharing IRQ 10 with 0000:00:1f.2
[ 15.269888] ipw2200 0000:03:03.0: sharing IRQ 10 with 0000:00:1f.3
[ 15.269900] ipw2200 0000:03:03.0: sharing IRQ 10 with 0000:03:01.2
[ 15.269970] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 15.270007] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[ 16.643176] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[ 16.644863] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 16.645575] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[ 16.646162] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[ 16.646902] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[ 16.835104] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 19.465849] Intel ICH 0000:00:1e.2: found PCI INT A -> IRQ 11
[ 19.465859] Intel ICH 0000:00:1e.2: sharing IRQ 11 with 0000:00:1d.0
[ 19.465868] Intel ICH 0000:00:1e.2: sharing IRQ 11 with 0000:00:1d.7
[ 19.465882] Intel ICH 0000:00:1e.2: sharing IRQ 11 with 0000:01:00.0
[ 19.465920] Intel ICH 0000:00:1e.2: setting latency timer to 64
[ 20.292015] intel8x0_measure_ac97_clock: measured 55472 usecs (2672 samples)
[ 20.292019] intel8x0: clocking to 48000
[ 26.580887] ppdev: user-space parallel port driver
[ 26.762543] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 26.762547] Bluetooth: BNEP filters: protocol multicast
[ 26.954085] Bridge firewalling registered
[ 27.964656] tg3 0000:03:00.0: firmware: requesting tigon/tg3_tso5.bin
[ 28.027724] tg3 0000:03:00.0: PME# disabled
[ 28.334294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 38.400010] eth1: no IPv6 routers present
[ 89.528013] Marking TSC unstable due to cpufreq changes
[ 89.672022] Clocksource tsc unstable (delta = -89970642 ns)
[ 225.832436] tg3 0000:03:00.0: PME# enabled
[ 225.960972] tg3 0000:03:00.0: PME# disabled
[ 226.296855] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 237.216024] eth1: no IPv6 routers present
[ 280.508441] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 280.508445] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 280.508448] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
 
nm-settings
 
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=true

---

### Post by searchfgold6789 on 2010-12-02
My network card is much older and simpler (I.E. 2 or 3 components on the board :) ); and it install it again unless I plug it into a different PCI slot, rearrange all my other PCI cards, and restart... twice.
So, maybe some major fooling around may be in order. Otherwise google for drivers.

---

