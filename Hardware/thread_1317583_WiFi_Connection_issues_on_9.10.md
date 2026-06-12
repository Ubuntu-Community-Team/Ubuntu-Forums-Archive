---
title: "WiFi Connection issues on 9.10"
date: 2009-11-06
forum: Hardware
---

### Post by Swamprat2010 on 2009-11-06
Hello All,

Some issues no that I have upgraded from 9.04 to 9.10. My WiFi will log on and then drop off and fail to detect anythig after that. The length of time it stays connected is to the wirelss is random. 9.04 did not have this issue, and nither does windows in part confirming its something to do with 9.10 i think.
I read around the posts to see if anyone else was having the same issue and one suggestion was to change from that standard network manager to Wicd whic i did but no difference. Any help would be good =)) wifi is usefull on the laptop.  

> 
Laptop: Acer Aspire 5536

Kubuntu: KDE: 3.5.10
Qt: 3.3.8b
Kernel: 2.6.31-14-generic 
#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
I hope the following information helps somewhat. It was taken when the connection was working no doubt it will drop soon so will try to post asap =))


> ~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602            
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


> ~$ sudo lshw -C network
  *-network                                   
       description: Ethernet interface        
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation                   
       physical id: 0                                 
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1d:72:f5:09:46
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0300000-f030ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:75:f6:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0400000-f040ffff> ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:f5:09:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              
          Interrupt:16                                        

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:75:f6:3e
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe75:f63e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:141760673 (141.7 MB)  TX bytes:4985159 (4.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-75-F6-3E-37-35-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Swamprat2010 on 2009-11-07
It might be my bad in fact as it has been stable now for about 24h plus. I think that it might have been an issue with gufw.Desktop   which did not uninstall properly.
The only change i made just before the post was to delete the file mentioned above.

Is that a likely cause?

Thanks,
Richard

---

