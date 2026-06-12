---
title: "DSL Router disappeared"
date: 2008-05-27
forum: Hardware
---

### Post by GroundZero on 2008-05-27
HI!
I have a problem with my DSL Router.Everything was fine,I could connect to the internet easily everything was working until Ubuntu gave me message that it can't find my device.I tried again 
"sudo pppoeconf" but it yust hangs and tells me that it can't find my device and then he sleeps.
I also tried:

#sudo dhclient
Listening on LPF/eth0/00:0d:61:46:63:47
Sending on LPF/eth0/00:0d:61:46:63:47
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping. 

And:

#sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:0d:61:46:63:47
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xc800

eth0:avahi Link encap:Ethernet HWaddr 00:0d:61:46:63:47
inet addr:169.254.4.145 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:20 Base address:0xc800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1628 errors:0 dropped:0 overruns:0 frame:0
TX packets:1628 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:81704 (79.7 KB) TX bytes:81704 (79.7 KB)

---

