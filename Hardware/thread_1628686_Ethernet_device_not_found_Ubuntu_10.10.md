---
title: "Ethernet device not found Ubuntu 10.10"
date: 2010-11-23
forum: Hardware
---

### Post by jeromiep on 2010-11-23
Hi I'm having trouble getting my Ethernet port to work on ubuntu 10.10. I'm new to ubuntu. I've looked under System Info and it show my device: Broadcom Corporation BCM4401 100Base-T (rev 01) but when I look in Network connections it doesn't show up. any help?

---

### Post by Fafler on 2010-11-23
If you connect a cable, it should show up as eth0.

You can open a terminal and type
```
ifconfig eth0
```
It should return something like
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ee000000-ee020000 

```
This means the interface is there, but hasn't been configured.
If the interface has been configured by a DHCP server, it should be more similar to
```
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:176.16.1.14  Bcast:176.16.255.255  Mask:255.255.0.0
          inet6 addr: xxx::xxx:xxx:xxx:xxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:907325506 (907.3 MB)  TX bytes:45911742 (45.9 MB)

```

---

