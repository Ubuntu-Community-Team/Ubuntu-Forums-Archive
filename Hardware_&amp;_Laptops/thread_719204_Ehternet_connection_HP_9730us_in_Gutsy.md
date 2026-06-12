---
title: "Ehternet connection HP 9730us in Gutsy"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by Jurgen1907 on 2008-03-08
Hi Guys,

I have a new laptop and can't connect to the internet.
I use Gutsy on a HP 9730us, 3 gig memory. 2.2 gig AMD Turion 64x2  Tl-64 processor.

jurgen@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
jurgen@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr FE:8E:F2:24:1B:00  
          inet6 addr: fe80::fc8e:f2ff:fe24:1b00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:325071 (317.4 KB)  TX bytes:5335 (5.2 KB)
          Interrupt:19 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr FE:8E:F2:24:1B:00  
          inet addr:169.254.3.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45856 (44.7 KB)  TX bytes:45856 (44.7 KB)

Can anyone please help me?
Thank in advance.

---

### Post by oldsoundguy on 2008-03-08
hate to ask a silly question, but did you go into system> administration> network> highlight wired connection> properties> enable roaming mode?

That is the way my hard wired unit works.

---

### Post by Yellow Pasque on 2008-03-08
What kind of chipset is it and do you have drivers loaded? IS the link detected? Run this:
```
sudo lshw -C network
sudo ethtool eth0
```

EDIT: Ok, it looks like you're sending/receiving packets. Do you know if you use a static IP or a dynamically assigned one through DHCP?

---

### Post by Jurgen1907 on 2008-03-09
Enable roaming is on. 

I copied and pasted the following, maybe this will help you know what the problem is.

jurgen@ubuntu:~$ sudo lshw -C network
[sudo] password for jurgen:
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: fe:8e:f2:24:1b:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
jurgen@ubuntu:~$ sudo lshw -C network
[sudo] password for jurgen:
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: fe:8e:f2:24:1b:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

