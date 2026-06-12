---
title: "Ubuntu 11.04 and atheros ar5001 wifi chip problem to scan wifi"
date: 2011-04-10
forum: Hardware
---

### Post by lupoxx on 2011-04-10
Hi men,
alfter the upgrade of ubuntu from 10.10 to 11.04 beta my network card is a bit unstable.

The driver ath5k i correctly mounted into the kernel, the interface i properly detected (and showed in iwconfig list) and the network card is up.

The main problem is at the startup and resume, in this cases the network manager don't show the available wifi network (same scenario with iwlist wlan0 scan command) for a lot of minutes (5-10 minutes... ). After the network card hung up my home wifi network and no other problem emerge since next reboot.

Some idea to solve this situation?

---

### Post by Dago_Ô on 2011-05-29
Same problem here... since 10.10 my Atheros 5001 doesn't detect any wifi network, but hardware seems to be properly detected and installed

---

### Post by randomsusers on 2011-06-03
I have a similar problem with 10.04 and my HP Pavillion DV7-1451nr. The common feature is, of course, the AR5001 Wireless adapter. I can find no error messages, but I still can't make a connection with anything. Here are some commands and the results:

tom@Owl:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:23:5a:b7:b0:4d
inet addr:192.168.100.97 Bcast:192.168.255.255 Mask:255.255.0.0
inet6 addr: fe80::223:5aff:feb7:b04d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6481 errors:0 dropped:0 overruns:0 frame:0
TX packets:3911 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5672731 (5.6 MB) TX bytes:577116 (577.1 KB)
Interrupt:28 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:960 (960.0 B) TX bytes:960 (960.0 B)

wlan0 Link encap:Ethernet HWaddr 00:26:5e:2d:20:6c
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

tom@Owl:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID: off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Managementff

tom@Owl:~$ sudo lshw -C network
[sudo] password for tom:
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:09:00.0
logical name: wlan0
version: 01
serial: 00:26:5e:2d:20:6c
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet 
physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes 
wireless=IEEE 802.11bg
resources: irq:18 memory:d1100000-d110ffff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:0a:00.0
logical name: eth0
version: 02
serial: 00:23:5a:b7:b0:4d
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom 
ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 
driverversion=2.3LK-NAPI duplex=full ip=192.168.100.97 latency=0 
link=yes multicast=yes port=MII speed=100MB/s
resources: irq:28 ioport:2000(size=256) 
memory:d1010000-d1010fff(prefetchable) 
memory:d1000000-d100ffff(prefetchable) 
memory:d1020000-d103ffff(prefetchable)

[Extract from] lspci -vvnn
09:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137a]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath5k


Any suggestions would be appreciated.

---

### Post by karmic-koala on 2011-07-15
Just a quick note to say I too am affected by this. [Atheros 5001].

A temporary workaround is to manually feed details of your wifi network and then 'connect to a hidden network' - select the pre configured network here. Not ideal but gets me connected every time.

---

### Post by louisgonick on 2011-07-17
I have Natty but this commands turn on my AR5001 card:
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

---

### Post by arungupta2008 on 2013-02-26
Thanx For the last Post It's Working

---

### Post by codemaniac on 2013-02-26
Thread closed.

@arungupta2008

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Moreover Ubuntu 11.04 had reached EOL on October 28, 2012, you can consider upgrading to a newer version that is supported.

Thanks and best of luck.

---

