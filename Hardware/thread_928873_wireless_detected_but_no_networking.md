---
title: "wireless detected but no networking"
date: 2008-09-24
forum: Hardware
---

### Post by ubuntergeist on 2008-09-24
hi,

After struggling for days and nights to have my wireless adapter detected by Hardy (8.04.1) when I finally managed to get the job done now Hardy just won't let me connect to the internet.

I configured my wireless connection using the network manager, it says that connection is established but I have no network (I can't ping, I can't surf).

here is the output of some usual commands I was told to run :

ifconfig :
```
amine@amine-laptop:/media/disk$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107048 (104.5 KB)  TX bytes:107048 (104.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:37:13:76  
          inet6 addr: fe80::221:63ff:fe37:1376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48011 (46.8 KB)  TX bytes:2706 (2.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-37-13-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

ifup and ifdown
```

amine@amine-laptop:/etc$ sudo ifup wlan0 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:37:13:76
Sending on   LPF/wlan0/00:21:63:37:13:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory

```

```

amine@amine-laptop:/media/disk$ sudo ifdown wlan0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:37:13:76
Sending on   LPF/wlan0/00:21:63:37:13:76
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory


```

I have noticed that many people on different forums around the world complain about such a behavior in Hardy.

Is there a solution to this problem ?

thank you.

---

