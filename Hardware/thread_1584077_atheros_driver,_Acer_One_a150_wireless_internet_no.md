---
title: "atheros driver, Acer One a150 wireless internet not working after kernel update"
date: 2010-09-28
forum: Hardware
---

### Post by Zerberus on 2010-09-28
I have installed the latest version of maverick, I also used the latest update from

[https://help.ubuntu.com/community/Wi...Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

> options ath_pci rfkill=0 			 		


I have also used Dr. Kurians version of installation with the above link:

http://ubuntuforums.org/showthread.php?t=1309072

WICD will just not show any ESSID at all!



however my problem currently is as follows:

> 
			 				  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:a3:d3:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.1.69 latency=0 link=yes  multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:31010000-31010fff memory:31000000-3100ffff memory:31020000-3103ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
   **    logical name: wifi0**
       version: 01
       serial: 00:22:69:11:c8:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:35200000-3520ffff 			 		



[QUOTE][**ath0 **     Link encap:Ethernet  HWaddr 00:22:69:11:c8:88  
          inet6 addr: fe80::222:69ff:fe11:c888/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:a3:d3:ae  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea3:d3ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8088060 (8.0 MB)  TX bytes:1328787 (1.3 MB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
[B]
wifi0  [/B]   Link encap:UNSPEC  HWaddr 00-22-69-11-C8-88-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:95770 (95.7 KB)
          Interrupt:18  			 		

/QUOTE]
so i supposedly have two wifi networks one is wifi0 and one is  ath0, the problem is atheros is not set as ath0 but as wifi0, so how can  i circumvent the problem that it becomes ath0. Yes I did try to change  the setting in wicd from ath0 to wifi0 as well I restarted it, I also  pressed on the slider for the wifi (altho we all know the lights aren't  working), so pretty much i tried everything, I even reinstalled maverick  from scratch, as my operating system has a partition so no personal  files get deleted!

so the problem is I still can not connect to anything without wired  connection. And no wireless network shows up! The wireless was working  perfectly in lucid, however you just want to know how the newest netbook  edition is :razz:

---

### Post by Zerberus on 2010-09-28
The problem has become worse

---

