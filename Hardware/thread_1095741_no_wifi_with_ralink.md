---
title: "no wifi with ralink"
date: 2009-03-14
forum: Hardware
---

### Post by Softsky on 2009-03-14
brought a acer aspire 5335 laptop installed 8.10 ubuntu on it, everything works fine but wifi

installed madwifi hoping that it would fix it, no luck

spent hours google searching trying to find a fix, endless attempts at installing and enabling wifi with no results

i come to you with help as i use ubuntu for my studys at polytech and rather use linux tha windows, but i need wifi access for course material

below is info that might help anyone that can help me, im unsure on what to do next as i have tried both ath_pci and ath5k drivers with no luck

madwifi doesnt pick up the card at all, eth0 works fine

current laptop:

Acer Aspire 5335

build:

andy@andy-laptop:~$ uname -a
Linux andy-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

lspci -vvnn               ***edited for length***

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
	Subsystem: Acer Incorporated [ALI] Device [1025:013f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 2298
	Region 0: Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 Network controller [0280]: RaLink Device [1814:0781]
	Subsystem: Foxconn International, Inc. Device [105b:e002]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f8600000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

                               ***edit end***

andy@andy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:f0:f7:25
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.108 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 5e:f0:16:80:04:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

