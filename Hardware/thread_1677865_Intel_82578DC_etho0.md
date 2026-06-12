---
title: "Intel 82578DC etho0"
date: 2011-01-29
forum: Hardware
---

### Post by caddoo on 2011-01-29
Hello,

I'm having a few issues with the ethernet connection in ubuntu (wireless works fine).

It is very temperamental (rebooting sometimes fixes it).

The network situation. 


[LIST]
[*]The computer is physically connected to a repeater bridge.
[/LIST]

[LIST]
[*]The wireless connection also connect to this (via wireless)
[/LIST]
The output of my ifconfig:

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17208 (17.2 KB)  TX bytes:17208 (17.2 KB)

wlan0     Link encap:Ethernet  HWaddr 94:0c:6d:c9:3c:c8  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::960c:6dff:fec9:3cc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45648681 (45.6 MB)  TX bytes:3483416 (3.4 MB)

```So there is no etho0 listed.

What steps can I take to fix this.

Thanks,

Matt

---

