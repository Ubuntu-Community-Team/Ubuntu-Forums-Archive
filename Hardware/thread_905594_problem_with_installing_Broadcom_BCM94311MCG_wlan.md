---
title: "problem with installing Broadcom BCM94311MCG wlan"
date: 2008-08-30
forum: Hardware
---

### Post by Aukikco on 2008-08-30
I did a fresh install of Ubuntu 8.04 on a friend's computer. I cannot get the wlan (Broadcom BCM94311MCG) to work - ifconfig doesn't find wlan0 at all.

The wlan modem worked just some hours ago on a vista installation, so the problem is not the hardware.

ifconfig outputs:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:86:86:f2  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe86:86f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2251 errors:0 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2320787 (2.2 MB)  TX bytes:325152 (317.5 KB)
          Interrupt:17 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50500 (49.3 KB)  TX bytes:50500 (49.3 KB)

```

---

### Post by pytheas22 on 2008-08-30
I think that you still need to use ndiswrapper to get Broadcom 94311 cards to work, because the native drivers still don't support them well.  There are instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"); please give them a try and let us know how it goes.  Make sure to pay attention to the "Hardy Bug Fix" section.

If you still can't get online after following that tutorial, please post this information here:
```

lshw -C Network
ndiswrapper -l
lspci -nn
iwlist scan
```

---

