---
title: "IBM ThinkPad T40 + wired issues"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by Infeliz on 2006-06-24
Hey

I've a problem with my connection eth0. Network works fine in the morning to the afternoon. In the evening network breaks and wont connect anymore. When I try again in the morning it works fine.

Right now I've sama problem, network works fine in my other computer which has windows XP Pro SP2.

I've 2 computer and router, I use pppoe.

```

kimmo@kimmo:~$ route -n
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

212.50.222.12   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


```

```

eth0      Link encap:Ethernet  HWaddr 00:09:6B:2D:6A:76
          inet6 addr: fe80::209:6bff:fe2d:6a76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:1100980 (1.0 MiB)  TX bytes:242978 (237.2 KiB)
          Base address:0x8000 Memory:c0220000-c0240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:85.217.17.232  P-t-P:212.50.222.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1048536 (1023.9 KiB)  TX bytes:191494 (187.0 KiB)


```

```


kimmo@kimmo:~$ dmesg |grep eth0
[17179589.908000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179591.544000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[17179609.640000] eth0: no IPv6 routers present
[17181509.876000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[17181514.796000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex

```

---

