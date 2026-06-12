---
title: "Installing 3 Quad-port NICs  HELP!"
date: 2009-08-19
forum: Hardware
---

### Post by redscorpion69 on 2009-08-19
I have 3 quad port nics i want to install in ubuntu. 

lspci shows that all 12 ports are here:

0a:08.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0a:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0a:0a.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0a:0b.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0b:08.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0b:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0b:0a.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0b:0b.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0c:08.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0c:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0c:0a.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0c:0b.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)

but, ifconfig -a shows only up to eth8 (eth0 is integarted on mobo i use for internet connection).


eth1      Link encap:Ethernet  HWaddr xxxxxxxxxxxxx  
          inet6 addr: xxxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:16 Base address:0x9e00 

eth2      Link encap:Ethernet  HWaddr xxxxxxxxxxxxxx  
          inet6 addr: xxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152254 (152.2 KB)  TX bytes:3204 (3.2 KB)
          Interrupt:17 Base address:0x9c00 

eth3      Link encap:Ethernet  Hxxxxxxx
          inet6 addr: xxxxxxxxxxxScope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:18 Base address:0x9a00 

eth4      Link encap:Ethernet  HWaddr xxxxxxxxxxx 
          inet6 addr: xxxxxxxxxxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151286 (151.2 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:19 Base address:0x9800 

eth5      Link encap:Ethernet  HWaddr xxxxxxxxxxx 
          inet6 addr: xxxxxxxxxxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152600 (152.6 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:17 Base address:0x8e00 

eth6      Link encap:Ethernet  HWaddr xxxxxxxxxxxxx 
          inet6 addr: fxxxxxxxxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151978 (151.9 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:18 Base address:0x8c00 

eth7      Link encap:Ethernet  HWaddrxxxxxxxxxxxx  
          inet6 addr: fxxxxxxxxxxxxxxx4 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152254 (152.2 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:19 Base address:0x8a00 

eth8      Link encap:Ethernet  HWaddr xxxxxxxxxxxxx  
          inet6 addr: xxxxxxxxxxxxxxx Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151632 (151.6 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:16 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 3e:4e:e0:fb:fa:96  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The question:

How do i install eth9-eth12 for other 4 ports, and how do i find their mac address at all?


THX!

---

### Post by redscorpion69 on 2009-08-19
Sorry for bump, need this info asap :(

:( nobody?

---

### Post by redscorpion69 on 2009-08-20
bump, thank you !

---

### Post by redscorpion69 on 2009-08-20
/

---

### Post by redscorpion69 on 2009-08-21
I find it hard that there is noone who can at least point me in the right direction..

---

### Post by bear24rw on 2009-08-21
what does your /etc/interfaces look like?

---

### Post by redscorpion69 on 2009-08-21
Thx for help! :KS


you mean /etc/network/interfaces ?

auto lo
iface lo inet loopback

thats it.

cards seem to be installed (all 12 ports):

***lspci -vvnn***

0a:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 9e00 [size=256]
	Region 1: Memory at fcfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0a:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 9c00 [size=256]
	Region 1: Memory at fcffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0a:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 9a00 [size=256]
	Region 1: Memory at fcffd000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0a:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 9800 [size=256]
	Region 1: Memory at fcffc000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0b:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 8e00 [size=256]
	Region 1: Memory at fceff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0b:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 8c00 [size=256]
	Region 1: Memory at fcefe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0b:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 8a00 [size=256]
	Region 1: Memory at fcefd000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0b:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 8800 [size=256]
	Region 1: Memory at fcefc000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-velocity
	Kernel modules: via-velocity

0c:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 14
	Region 0: I/O ports at 7e00 [size=256]
	Region 1: Memory at fd0ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: via-velocity

0c:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 15
	Region 0: I/O ports at 7c00 [size=256]
	Region 1: Memory at fd0fe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: via-velocity

0c:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at 7a00 [size=256]
	Region 1: Memory at fd0fd000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: via-velocity

0c:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
	Subsystem: VIA Technologies, Inc. Device [1106:0110]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 7800 [size=256]
	Region 1: Memory at fd0fc000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: via-velocity


Maybe that IRQ has something to do with it?

---

### Post by bear24rw on 2009-08-21
I think you might wanna add them all to the /etc/network/interfaces file manually. I honestly dont know how to do that off top of my head by im sure google can help

---

### Post by redscorpion69 on 2009-08-21
I tried but couldnt find anything on this matter.

I'm not that good with ubuntu so i don't know how to add them.

I noticed in lspci that IRQ setting for 16,17,18,19 is repeating twice? Maybe that has something to do with?

---

### Post by redscorpion69 on 2009-08-21
bump :(

---

### Post by redscorpion69 on 2009-08-25
BUMP FOR THE LAST TIME...

Anyone good enough to give some ideas at least!?

dmesg

.....

[ 5.598403] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
[ 5.598405] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[ 5.598406] Copyright (c) 2004 Red Hat Inc.
[ 5.598416] via-velocity 0000:0a:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5.599409] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.599411] eth1: Ethernet Address: 00:0C:42:1A:0E:94
[ 5.611441] ohci1394 0000:09:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5.613027] via-velocity 0000:0a:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5.613885] eth2: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.613887] eth2: Ethernet Address: 00:0C:42:1A:0E:95
[ 5.629031] via-velocity 0000:0a:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5.630241] eth3: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.630244] eth3: Ethernet Address: 00:0C:42:1A:0E:96
[ 5.645025] via-velocity 0000:0a:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 5.645946] eth4: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.645948] eth4: Ethernet Address: 00:0C:42:1A:0E:97
[ 5.661019] via-velocity 0000:0b:08.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5.661132] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18] MMIO=[fd1ff000-fd1ff7ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 5.661757] eth5: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.661759] eth5: Ethernet Address: 00:0C:42:1A:0E:A4
[ 5.677019] via-velocity 0000:0b:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5.677792] eth6: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.677794] eth6: Ethernet Address: 00:0C:42:1A:0E:A5
[ 5.693017] via-velocity 0000:0b:0a.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 5.693792] eth7: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.693793] eth7: Ethernet Address: 00:0C:42:1A:0E:A6
[ 5.709018] via-velocity 0000:0b:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5.709828] eth8: VIA Networking Velocity Family Gigabit Ethernet Adapter
[ 5.709830] eth8: Ethernet Address: 00:0C:42:1A:0E:A7
[ 5.725011] via-velocity 0000:0c:08.0: already found 8 NICs.
[ 5.725017] via-velocity 0000:0c:09.0: already found 8 NICs.
[ 5.725022] via-velocity 0000:0c:0a.0: already found 8 NICs.
[ 5.725026] via-velocity 0000:0c:0b.0: already found 8 NICs.
.......

Why is it giving last 4 lines ?

Tried Ubuntu, Kubuntu, Fedora, they all read just 8 ports..

---

