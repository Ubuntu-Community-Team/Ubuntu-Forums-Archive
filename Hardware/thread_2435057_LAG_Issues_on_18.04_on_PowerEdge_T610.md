---
title: "LAG Issues on 18.04 on PowerEdge T610"
date: 2020-01-15
forum: Hardware
---

### Post by virgil1804 on 2020-01-15
Hello,

let me start by saying that I have used this forum effortlessly for years and have always been able to find appropriate solutions  for every issue that I have come across, until now.  I have read countless threads with countless solutions that have been unsuccessful in resolving my particular issue so with great hope I create my first forum thread! Wish me luck.


I am unable to figure out to get 802.3ad Link Aggregation to work properly in Bionic Beaver!  Each time I get one thing working another thing won't.  For example currently I am sitting here with a working bond0, but only have access to the LAN, no internet access.  Any and all suggestions, expertise, or criticisms would be welcomed and appreciated.

Here is my /proc/net/bonding/bond0;

Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer3+4 (1)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0


802.3ad info
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: 00:26:b9:2d:cc:f5
Active Aggregator Info:
    Aggregator ID: 2
    Number of ports: 2
    Actor Key: 9
    Partner Key: 54
    Partner Mac Address: 04:a1:51:87:9a:74


Slave Interface: eno2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:26:b9:2d:cc:f5
Slave queue ID: 0
Aggregator ID: 2
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 0
Partner Churned Count: 0
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:26:b9:2d:cc:f5
    port key: 9
    port priority: 255
    port number: 1
    port state: 63
details partner lacp pdu:
    system priority: 32768
    system mac address: 04:a1:51:87:9a:74
    oper key: 54
    port priority: 128
    port number: 6
    port state: 61


Slave Interface: eno1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:26:b9:2d:cc:f3
Slave queue ID: 0
Aggregator ID: 2
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 0
Partner Churned Count: 0
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:26:b9:2d:cc:f5
    port key: 9
    port priority: 255
    port number: 2
    port state: 63
details partner lacp pdu:
    system priority: 32768
    system mac address: 04:a1:51:87:9a:74
    oper key: 54
    port priority: 128
    port number: 5
    port state: 61


And my /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eno1
iface eno1 inet manual
    bond-master bond0
    
auto eno2
iface eno2 inet manual
    bond-master bond0


auto bond0
iface bond0 inet static
address 192.168.1.201
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4


bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves eno1 eno2
bond-downdelay 0
bont-updelay 0
bond-xmit_hash_policy 1



 

I am currently running Ubuntu 18.04 (Desktop) on a Dell PowerEdge T610 server.

If you require more info to assist in diagnostics I would be glad to provide what I can.  Thank you ll in advance I have no doubts this will get resolved quickly


A little more info that may be helpful;

I am NOT able to ping google.com - returns: ping: google.com: Name or service unknown
I am able to ping My router by IP
I am able to ping 8.8.8.8

*-network:0               
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eno1
       version: 20
       serial: 00:26:b9:2d:cc:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.6 duplex=full firmware=bc 4.6.4 NCSI 1.0.6 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1Gbit/s
       resources: irq:32 memory:d6000000-d7ffffff
  *-network:1
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: eno2
       version: 20
       serial: 00:26:b9:2d:cc:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.6 duplex=full firmware=bc 4.6.4 NCSI 1.0.6 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1Gbit/s
       resources: irq:33 memory:d8000000-d9ffffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: bond0
       serial: 00:26:b9:2d:cc:f5
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=bonding driverversion=3.7.1 duplex=full firmware=2 ip=192.168.1.201 link=yes master=yes multicast=yes

---

