---
title: "Wireless trouble on Lenovo ThinkPad R60e"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by Shron on 2008-01-22
Hi everybody,

I am newbie for Ubuntu. I also have trouble with the wireless access. I tried to google my problem and search in our forum. But I can't find an answer. Could you please help me?

Related information:

Lenovo ThinkPad R60e.
Ubuntu 7.10
Router: Netgear MR814V2

In windows xp, I use Key Index 3. I didn't find anywhere to input this in Ubuntu. I am so confused! The wireless should be WEP. I can see the Wireless Networks list. But I couldn't connect.

In my Restricted Driver Manager, there appears the 'Intel(R) PRO/Wireless 3945 Network Connection driver for Linux'.

Here is my terminal 'ifconfig' output:
eth0 Link encap:Ethernet HWaddr 00:163:2F:0B:EF
inet addr:192.168.0.8 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::216:d3ff:fe2f:bef/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
RX packets:1526 errors:0 dropped:0 overruns:0 frame:0
TX packets:1441 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1385957 (1.3 MB) TX bytes:210841 (205.8 KB)
Interrupt:20

eth1 Link encap:Ethernet HWaddr 00:18E:4B:35:BF
inet6 addr: fe80::218:deff:fe4b:35bf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:23 errors:40 dropped:31435 overruns:0 frame:0
TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:12504 (12.2 KB) TX bytes:28212 (27.5 KB)
Interrupt:21 Base address:0xa000 Memory:edf00000-edf00fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:319 errors:0 dropped:0 overruns:0 frame:0
TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:24460 (23.8 KB) TX bytes:24460 (23.8 KB)

And my iwconfig output:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:"BBQ"
Mode:Managed Frequency=2.422 GHz Access Point: 00:09:5B:B0:9D:0E
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:32876 Missed beacon:0

Please Help me! Thanks a lot!

---

