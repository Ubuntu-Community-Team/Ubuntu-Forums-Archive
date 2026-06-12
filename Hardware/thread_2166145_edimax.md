---
title: "edimax"
date: 2013-08-07
forum: Hardware
---

### Post by johnnyelias on 2013-08-07
Hello . my english not good
I have extenal wirlees card . edimax 7612hnp . Two years ago it was working on windows
I am trying to run it on ubuntu 13.10 or ubuntu 12.04 LTS
I don't know where is the problem
is it the driver?
is it the card it self?
is it the cable?
I don't know what to do
please help me

---

### Post by newbie-user on 2013-08-08
Need more info about the NIC. Please post the output of
```
lshw -class network
```

---

### Post by johnnyelias on 2013-08-08
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: mon.wlan0
       version: 01
       serial: 48:5d:60:3b:2f:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=ath9k driverversion=3.10.0-6-generic firmware=N/A ip=10.10.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2c00000-d2c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: bc:ae:c5:d4:05:f4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:48 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)

---

### Post by newbie-user on 2013-08-08
Try installing the wireless backports modules:

for 64-bit OS:
```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```

for 32-bit OS:
```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic-pae
```

---

### Post by johnnyelias on 2013-08-08
[QUOTE=newbie-user;12750444]Try installing the wireless backports modules:

for 64-bit OS:
```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```


linux-backports-modules-cw-3.8-precise-generic is already the newest version

---

### Post by johnnyelias on 2013-08-08
this is what [COLOR=#ff0000]lsusb[/COLOR] command return


[COLOR=#ff0000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b1e5 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0b05:1751 ASUSTek Computer, Inc. BT-253 Bluetooth Adapter
Bus 002 Device 003: ID 046d:c058 Logitech, Inc. M115 Mouse[/COLOR]


this is what [COLOR=#ff0000]ifconfig[/COLOR] return

[COLOR=#ff0000]eth0      Link encap:Ethernet  HWaddr bc:ae:c5:d4:05:f4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fed4:5f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8765964 (8.7 MB)  TX bytes:1644075 (1.6 MB)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48356 (48.3 KB)  TX bytes:48356 (48.3 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:3b:2f:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]

---

### Post by newbie-user on 2013-08-09
Delete any existing wireless network that you have in network manager. Also, check /etc/network/interfaces to be sure that your wireless connection is set up for a dynamic ip instead of a static ip.

---

### Post by johnnyelias on 2013-08-10
explain what is meant by (Delete any existing wireless network that you have in network manager)
please

---

