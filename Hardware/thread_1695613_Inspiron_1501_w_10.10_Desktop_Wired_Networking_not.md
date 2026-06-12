---
title: "Inspiron 1501 w/ 10.10 Desktop: Wired Networking not working?"
date: 2011-02-26
forum: Hardware
---

### Post by madhartigan on 2011-02-26
Having trouble with getting my wired network interface to be recognized.

Here's the output of ifconfig:

```
darryl@DELL1501:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:cd:1d:ff  
          inet addr:192.168.0.123  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fecd:1dff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3946 errors:0 dropped:0 overruns:0 frame:8324
          TX packets:3716 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3330316 (3.3 MB)  TX bytes:692868 (692.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53264 (53.2 KB)  TX bytes:53264 (53.2 KB)
```



Here's the output of ifconfig **-a**:

```
darryl@DELL1501:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:cd:1d:ff  
          inet addr:192.168.0.123  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fecd:1dff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3962 errors:0 dropped:0 overruns:0 frame:8558
          TX packets:3739 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3331869 (3.3 MB)  TX bytes:694672 (694.6 KB)
          Interrupt:18 

eth1-eth0 Link encap:Ethernet  HWaddr 00:19:b9:5c:a7:b8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53264 (53.2 KB)  TX bytes:53264 (53.2 KB)
```


Why isn't my wired connection being automatically recognized?  I know that eth0 is my wireless connection.  What is eth0-eth1?  I'm assuming that eth0-eth1 is my wired connection?  I'm not sure.  The two leds on the network adapter's port are amber and orange/red.  Usually there's a green one so that's another weird aspect to this situation.  Don't know if that helps but wanted to give all the details.

I'm sure I'm just doing something wrong or have a configuration file that needs to be modified of something.  I'm just new at this so I need some help.


Thank you for any help that can be offered.

---

### Post by madhartigan on 2011-02-26
*bump*

---

### Post by madhartigan on 2011-02-26
Here are the results of lshw:

```
darryl@DELL1501:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:cd:1d:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.123 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c0200000-c0203fff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1-eth0
       version: 02
       serial: 00:19:b9:5c:a7:b8
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:21 memory:c0300000-c0301fff

```


Why is my ethernet port showing as disabled?  How do I enable it?


I don't know if I have the network monitor running properly or not.  This may have affected whether my ethernet port is automatically being configured.


Any help would be, well . . . . helpful.


Thanks!

---

### Post by JeffCBR on 2011-02-26
Post the results of:

iwconfig

and

cat /etc/network/interfaces

---

