---
title: "Compaq CQ60-419WM w/ Atheros AR5001 - wireless is disabled"
date: 2010-10-29
forum: Hardware
---

### Post by dataczar on 2010-10-29
Hello

I have been a user and fan of Ubuntu for several years, however, this is my first post.  For previous problems, I have been able to find answers from the wonderful forums.  However, this time I am stumped.  I have looked at 100's of posts from people with similar problems, but none of their solutions have worked yet.

I am working on a neighbor's computer, which is the Compaq CQ60-419wm with an Atheros AR5001 wireless card.  They purchased the computer with Windows Vista Basic on it, but after getting lots of viruses on it, they asked for my assistance.  I installed Ubuntu 10.04, and everything worked great for a couple of months.  They contacted me last week to say that they could no longer connect to their wireless internet on this computer.  I have looked all over the computer for a wireless switch/button, but have had no luck.  There is a button by the power button that is either blue or red.  At this time, the button is blue.

I have looked at several posts to find the solution with no luck.  I have even installed Ubuntu 10.10, thinking that maybe the newest kernel could solve the problem.  No such luck.

 lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:d0:2c:49
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.15.102 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:6e:26:6d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

In looking at the Network widget, wireless is disabled is greyed out.

Any assistance would be appreciated.  Please let me know if you need any additional information.

Thanks

dataczar

---

### Post by dmcf01 on 2010-10-30
I have a Compaq Presario CQ70 and have been experiencing the same issue. I started off with Ubuntu 8.04 and lost my wireless connection at some point with one of the updates (unfortunately I cannot recall at which version it stopped working).

I then stopped using Ubuntu for quite a while as I could not find a solution and did not have the time to investigate it any further. I started using Ubuntu again recently from 10.04 and the wireless card was enabled again. I then Reinstalled 10.10 and it worked for a few days but suddenly the wireless card became temperamental. For example when I enabled the wireless device using the laptop button at the top (which turns from red to blue to indicated that the wireless device has been turned on), the wireless device would remain disabled. If I then rebooted it would come back on. However, I turned it off again recently as I was using a wired connection and have been unable to get it to work again even if the LED wireless button is now stuck on blue indicating that the device is on.
As with the other user, when I click on the Network icon on the top taskbar the "wireless network" is greyed out and it says "device not ready". If I right click on it and 'enable wireless device' it still shows as "device not ready".  Iwconfig also shows the same message as the previous post:

iwcinfig:
o        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

sudo lshw -C network:

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:59:1f:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.234 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:16:54:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic-pae firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d2600000-d260ffff

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

i'd also like to clarify that the wired Ethernet connection works fine. and the Wireless device works fine under Windows 7 which I have on dual boot so I can safely rule out any hardware faults.

Dataczr, if you happen to find a solution then post it here, and I'll do the same.

---

### Post by byb3 on 2010-12-28
Yes the exact same thing has occurred to me while using Ubuntu 10.10 On a Compaq.  It must have happened with a recent update because it was fine before that.  I enable the wireless card but it just keeps saying 'Device not ready'.

I'm sorry guys, I've had to go back to Windows 7.  This is a laptop for my mother and she just can't live without wireless.  I tried moving her to Ubuntu but this is a game killer.

---

### Post by rhomany on 2010-12-29
I have almost exactly same problem with the Atheros AR5001 on a Samsung NC10 netbook since 10.10.
In my case the wireless says it's connected and I can ping the router, but there's no internet and no downloads.

---

### Post by rhomany on 2010-12-29
oops... dup

---

### Post by jeffymarts on 2010-12-29
I had this problem once and it had a simple solution in my case. On my CQ60 I accidentally shut of the wireless card by pressing the wireless indicator next to the power button. It's probably not going to work for you, but it's worth a shot.

---

### Post by randomsusers on 2011-06-03
I have similar problems with a Pavilion DV7-1451nr and the same AR5001 wireless. Mine is not greyed out, but I can't get it to connect to anything. I'd appreciate any suggestions anyone has. Not sure what else to do. Here's some command output:

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

tom@Owl:~$ sudo lspci -vvnn [extract from 15 page dump]
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

---

### Post by karlsalt on 2011-06-07
Got it! I had the same problem with my Compaq CQ60 running dual boot Ubuntu 11.04 (natty) and i forget what verswion of Suse Linux. In another forum I saw a solution using rfkill to investigate the status of wireless and turn off blocking. The software showed that my wireless device was softblocked. After installation, I ran "rfkill unblock 0" and "rfkill unblock 1" to unblock my #0 and #1 devices. I got a good connection after that. I still have no idea how they got blocked in the first place, but I'm keeping the file. Good luck!
[http://wireless.kernel.org/en/users/Documentation/rfkill?highlight=%28rfkill%29](http://wireless.kernel.org/en/users/Documentation/rfkill?highlight=%28rfkill%29)

---

### Post by louisgonick on 2011-07-17
I have Natty dualbooting with windows on the same laptop. This commands turn my card on. Apparently ubuntu does not work with this card. 
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

Hope this helped

---

### Post by Adan895 on 2011-07-27
> **louisgonick said:**
> i have natty dualbooting with windows on the same laptop. This commands turn my card on. Apparently ubuntu does not work with this card. 
Sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

hope this helped
i love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love youi love you

---

