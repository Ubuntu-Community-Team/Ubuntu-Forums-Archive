---
title: "Wire ethernet unable to connect Aspire One D255E"
date: 2011-04-06
forum: Hardware
---

### Post by darknature85 on 2011-04-06
Hello. I bought my wife an acer aspire one D255E recently. Now I did a clean installion by mistake (rushing myself) of Ubuntu Netbook edition 10.10. However to my finding I am having internet issues. One of the issues is how my internet detects that I plugged my Ethernet cord in and it will try to connect but after awhile it will drop connection. It doesn't allow me for even a bit of internet at all. I would like people to really help me in this predicament. Another question (really important don't skip) is how do I make software sourses read my flash drive like a CD. There is no option and googling for it gives me useless information. 

Anyways here is all the information you may need from me:

Sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:75:08:c7:30:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22192 (22.1 KB)  TX bytes:22192 (22.1 KB)

lspci
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

ifup eth0
Ignoring unknown interface eth0=eth0

cat /etc/network/interfaces
auto lo
iface lo inet loopback

cat/etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

dmesg |grep -e eth0 -e bcm
[   18.839666] ADDRCONF(NETDEV_UP): eth0: link is not ready
 
I understand as I am typing this to you my internet is not connected.

lshw -C Network
 *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:c7:30:e0
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:56000000-56003fff

lspci -nn
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)

If you need anymore information please ask away!

---

