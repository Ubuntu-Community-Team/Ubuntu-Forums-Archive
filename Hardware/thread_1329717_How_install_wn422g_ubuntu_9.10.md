---
title: "How install wn422g ubuntu 9.10"
date: 2009-11-17
forum: Hardware
---

### Post by tiagusto on 2009-11-17
hello recently i bought an pen wireless tp-link wn422g i have ubuntu 9.10 installed.
my problem is when i connect the pen to pc dont recgonize and i write on console:

```
lsusb
```shows

```

Bus 002 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```when write 

```
ifconfig -a
``````
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:cc:4c:52  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fecc:4c52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76288 errors:0 dropped:10 overruns:0 frame:0
          TX packets:51571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112067041 (112.0 MB)  TX bytes:4065123 (4.0 MB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



```
i have the system with latest kernel 2.6.31

please help me to install this drive!!
i appreciate!

Sorry  for may bad English!

---

### Post by dynofu on 2009-12-29
althou i cannot solve your problem, i am facing the same. this page might provide some hints. [http://linuxwireless.org/en/users/Drivers/ath9k_htc#Component_modules](http://linuxwireless.org/en/users/Drivers/ath9k_htc#Component_modules)

---

