---
title: "Ethernet controller not working"
date: 2009-07-08
forum: Hardware
---

### Post by WindPower on 2009-07-08
Hi, I just bought an Asus F50 laptop and the ethernet controller doesn't seem to work. The network manager says the eth0 interface, while present, is "unavailable".
lspci says "Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)".
I am on Kubuntu 9.04 64-bit but the same problem happened on Ubuntu 9.04 32-bit and Kubuntu 9.04 32-bit. Is there anything else I need to provide? How can I get my Ethernet controller to work?

---

### Post by WindPower on 2009-07-09
Here's the output of ifconfig, if it helps:
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:92:91:c6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3288 (3.2 KB)  TX bytes:3288 (3.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:87:63:02
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe87:6302/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:139915539 (139.9 MB)  TX bytes:4729070 (4.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-87-63-02-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
And here's dhclient:
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.                            
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/de:5c:6d:5f:e3:a6    
Sending on   LPF/pan0/de:5c:6d:5f:e3:a6    
Listening on LPF/wmaster0/                 
Sending on   LPF/wmaster0/                 
Listening on LPF/eth0/00:24:8c:92:91:c6    
Sending on   LPF/eth0/00:24:8c:92:91:c6    
Listening on LPF/wlan0/00:22:43:87:63:02   
Sending on   LPF/wlan0/00:22:43:87:63:02   
Sending on   Socket/fallback               
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6   
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4    
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by denzelz on 2009-08-22
I am having a similar problem with almost the identical dhclient and ifconfig. I've tried a lot of other solutions but it has not worked so far. Is there a known solution to this problem?

---

### Post by WindPower on 2009-08-22
No, I gave up and used the wireless interface instead. Slower, but it works, right?
Otherwise, I guess you can buy a USB Ethernet adapter.

---

