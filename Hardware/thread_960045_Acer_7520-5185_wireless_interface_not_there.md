---
title: "Acer 7520-5185 wireless interface not there"
date: 2008-10-27
forum: Hardware
---

### Post by Mannab on 2008-10-27
Hey guys, ofcourse another ubuntu(Hardy) noob here, i cant get my wireless to work any more, it used to and just suddenly didnt. 

heres my iwconfig :

maz@maz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I dont know if it can even see my wireless card, its just that when i open the network manager it doesnt even show my wireless connection, just shows the wired connection and the modem.

anyways here is my ifconfig:

maz@maz-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c8:24:66  
          inet addr:134.117.176.195  Bcast:134.117.176.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fec8:2466/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38069218 (36.3 MB)  TX bytes:3021095 (2.8 MB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88968 (86.8 KB)  TX bytes:88968 (86.8 KB)

if anyone could help me out that would be awesome. thanks

---

### Post by G_man on 2008-10-27
plz post the output of:
lspci

---

### Post by Mannab on 2008-10-28
maz@maz-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


I hope this helps

---

### Post by skaboss on 2008-11-15
I don't know if it's still relevant, but i have an Acer 7520G, and what worked for me is :
[LIST=1]
[*]Download the windows atheros driver from [here]("http://www.opendrivers.com/driver/271445/acer-aspire-7520-notebook-atheros-wireless-driver-7.3.1.42-windows-vista-free-download.html")
[*]install ndiswrapper from repositories
[*]disable all atheros support from System>Administration>Hardware drivers
[*]reboot
[*]run System>Administration>Windows WirelessDrivers, and select the path to the driver you downloaded
[*]reboot, and you should be ok !
[/LIST]

---

