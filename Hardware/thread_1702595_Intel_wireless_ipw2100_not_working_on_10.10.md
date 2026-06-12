---
title: "Intel wireless ipw2100 not working on 10.10"
date: 2011-03-08
forum: Hardware
---

### Post by oldunixguy on 2011-03-08
Using Ubuntu 10.10 on a Presario x1000 with an intel 2100 wireless.

When enabled, the wireless indicates "connected" even when it is impossible!

When it is in this (falsely) reported connected state I obtain the following:
dmesg:
```

[   20.599205] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   20.599211] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   20.635073] ipw2100 0000:02:02.0: PCI INT A -> Link[C0C5] -> GSI 5 (level, low) -> IRQ 5
[   20.635840] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   20.635869] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3.fw
[   47.860100] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3-i.fw
[   76.154290] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3.fw

...

[  796.658171] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3-i.fw

[  796.658108] eth1: Reseting on mode change.
[  798.516149] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  809.320056] eth1: no IPv6 routers present

```lspci:
```

02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```ifconfig:
```

eth1      Link encap:Ethernet  HWaddr 00:04:23:60:4c:91  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe60:4c91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9287 (9.2 KB)
          Interrupt:5 Base address:0xc000 Memory:90000000-90000fff 

```The wireless will do this regardless of whether there is a wireless access point turned on or not!

Also, I got identical results from trying Ubuntu 9.10.

Any advice is appreciated.
thanks.

---

