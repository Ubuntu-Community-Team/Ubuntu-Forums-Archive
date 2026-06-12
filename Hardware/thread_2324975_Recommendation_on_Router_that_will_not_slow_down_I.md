---
title: "Recommendation on Router that will not slow down Internet when using wifi"
date: 2016-05-18
forum: Hardware
---

### Post by Ralph L on 2016-05-18
I have an old Linksys wrt110 router.  It has 802.11n (draft) capability.  Internet speed tests show that, when I plug my computer directly into my cable modem, I get about 30Mbit/sec download and about 2.75Mbit/sec upload.  However, when I plug the router into the cable modem and access the Internet through the router's wifi, I get only 12 to 15 Mbit/sec download.  It cuts the download speed in half!!!  

Anybody got any recommendations of how I get rid of this router/wifi bottleneck?  An 802.11n router should handle this speed.  Could the fact that it is a Draft implementation be slowing it down???  If you recommend that I get a new router, would you give me specific model recommendations so that I don't buy another slow router??

Any help appreciated

---

### Post by efflandt on 2016-05-18
If you click on the WiFi icon at the top of your screen, and click on **Connection Information**, what does that show for your WiFi Speed? Maybe you have a weak signal that is not full speed. WiFi is similar to a hub in that if more than one thing tries to communicate at the same time, data can collide and have to be resent. When our WAP (wireless access point) was in the back of our warehouse and I only got weak 78 Mbps wireless-n speed, I only got about 25 Mbps Internet download speed. When I moved the WAP into our office and got 150 Mbps wireless, I got the full 57-58 Mbps download speed of our Internet connection. So from that I am guessing that it works best if your wireless speed is at least 3 times your Internet speed.

That is not an issue at home where even wireless-g at 54 Mbps is plenty for my 5.1 Mbps DSL.

---

### Post by Ralph L on 2016-05-19
efflandt,

Thanks for the response. I much appreciate it. You made me look at some things that I hadn't considered before.

  I have 3 laptop computers that I use.  The first is a Dell Latitude D610 (about 10 years old).  When I look at Connection Information I see that the speed varies from 36Mbps to 54Mbps--802.11 G range.  This indicates to me that my wifi card doesn't support 802.11N.  When I do lspci -vv I get:
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at dfcfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge

My second computer is also a Dell Latitude D610.  When I look at Connection Information, it seems to stick at 54Mbps--a little faster than the first computer, but still in the G range.  When I do lspci -vv I get:
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Dell B130 laptop integrated WLAN
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 6000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

My third computer is a Toshiba Satellite A215-S4697.  When I look at Connection Information, it varies between 9Mbps and 54Mbps.  When it is actually in use, it seems to usually be at 54Mbps.  When I do lspci -vv I get:
14:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k

My conclusion is that I don't need a new router.  I need new computer with 802.11N wifi cards or 802.11N wifi cards for my present computers.  Do you know of any N mini pci cards that would fit a Latitude D610.  I couldn't find any.

---

### Post by Ralph L on 2016-05-19
I can't seem to find an 802.11N card for my Dell D610 laptop, so another thought I had on how to get my download Internet speed up to 30Mbps, is to find an 802.11G card that will actually run at 30Mbps.  802.11G is supposed to run at 54Mbps, so there must be some cards that will actually run a 30Mbps.  My Dell Latitude D610 laptop uses a miniPCI card from what I read.  Can anybody recommend a Dell D610 "G" card that will run at at least 30Mbps.

---

### Post by Ralph L on 2017-01-18
See [https://ubuntuforums.org/showthread.php?t=2338890](https://ubuntuforums.org/showthread.php?t=2338890) for how I finally got an 802.11 a/b/g/n wifi card to work on my Dell Latitude D610.

---

### Post by wildmanne39 on 2017-01-18
Please do not cross post, thread closed!

From posting guidelines.
> Do not cross post, or post the same thing in multiple locations.

---

