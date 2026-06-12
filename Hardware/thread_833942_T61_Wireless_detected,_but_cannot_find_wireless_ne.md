---
title: "T61 Wireless detected, but cannot find wireless networks"
date: 2008-06-19
forum: Hardware
---

### Post by peterlauri on 2008-06-19
Hi,

I have a Lenovo T61 that have the wireless card detected. It seams like the Wireless is connected properly when I switch it on, as I can see it via ifconfig. But the list of availible networks is empty with both nm-applet and doing "iwlist scan". I am not sure what "wlan0     Failed to read scan data : Resource temporarily unavailable" means (part of iwlist scan output).

Complete output in the end of the message.

Thanks,
Peter

peternsn@peter:/data/webroot/HCAT/APPLIC$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:14:19:a9  
          inet addr:10.144.35.8  Bcast:10.144.35.255  Mask:255.255.254.0
          inet6 addr: fe80::21c:25ff:fe14:19a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8181958 (7.8 MB)  TX bytes:1961819 (1.8 MB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75500 (73.7 KB)  TX bytes:75500 (73.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:02:82:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-02-82-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

peternsn@peter:/data/webroot/HCAT/APPLIC$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

---

