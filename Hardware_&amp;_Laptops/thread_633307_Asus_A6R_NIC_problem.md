---
title: "Asus A6R NIC problem"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by fernando_lopes_jr on 2007-12-06
I just done a fresh install of ubuntu 7.10 on my asus a6r desktop every thing was working fine until a few minutes ago the nic stopped working I tryed to restart system but it still doesn't work. It just doesn't pick up a ip I don't understand.
The output from lspci is: 
> 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08 )
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
and from ifconfig -a
> eth0      Link encap:Ethernet  HWaddr 00:15:F2:22:7C:A7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x2c00 

eth1      Link encap:Ethernet  HWaddr 00:15:F2:1B:AD:F8  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe1b:adf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27202 errors:0 dropped:494 overruns:0 frame:0
          TX packets:16769 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36520961 (34.8 MB)  TX bytes:1221146 (1.1 MB)
          Interrupt:5 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:868 (868.0 b)  TX bytes:868 (868.0 b)

Could sameone give me a hand plz :(

---

### Post by njparton on 2007-12-07
Ubuntu is recognising 2 network adapters et0 and eth1. Do you actually have 2?

If not, follow my post just made here: [http://ubuntuforums.org/showthread.php?t=632155](http://ubuntuforums.org/showthread.php?t=632155)

---

### Post by fernando_lopes_jr on 2007-12-07
yes I have eth0 is wired and eth1 is wireless. Wireless is working fine.

---

### Post by Yellow Pasque on 2007-12-07
When you do an lsmod, do you see anything with 8139 in it?

---

