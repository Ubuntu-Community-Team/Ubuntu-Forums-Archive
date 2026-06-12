---
title: "IBM/Lenovo Thinkpad R51e irrecoverably loosing wifi connection"
date: 2010-11-03
forum: Hardware
---

### Post by ChuckyZ28 on 2010-11-03
p { margin-bottom: 0.08in; }  I have recently reformatted my HDD and installed ubuntu 10.04 alone(it had been dual boot windows XP) since the fresh install I have noticed that the wifi connection has been dropping out and will never recover. The only thing I can do to regain it is to restart the computer. The other thing I have noticed about it is the fact that sometimes it will work for hours sometimes it will loose the connection within a matter of min. In addition when it does fail, it no longer recognizes any networks at all. Here are the system specs 

**Machine: **
IBM Thinkpad R51e

**Wireless:**
Atheros AR5001X+ Wireless Network Adapter (rev 01)

**Interface:**
charles@charles-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Grandpa\xA0Ferguson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 94:44:52:72:83:B2   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**Module:**
No module found(unknown problem)

[B]Network Config
[/B]*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751F Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d3:2a:4a:3d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751f-v3.46a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:b0200000-b020ffff
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:18:5e:ee
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.4 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:b0300000-b030ffff

[B]Scan Networks
[/B]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

[B]Ubuntu Verson:
[/B]Ubuntu 10.04.1 LTS[B]

Kernel Verson
[/B]2.6.32-25-generic i686

**Restart Network**
* Reconfiguring network interfaces...                                                               [ OK ]

---

