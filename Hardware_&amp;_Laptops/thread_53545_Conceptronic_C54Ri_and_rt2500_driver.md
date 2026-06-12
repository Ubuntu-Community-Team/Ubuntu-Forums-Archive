---
title: "Conceptronic C54Ri and rt2500 driver"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by logan.bone on 2005-08-01
I had a wireless card (edimax EW-7128g) and I downloaded and compiled rt2500 driver. At the beginning, when I type iwconfig appears:

ra0     RT2500 Wireless  ESSID:"home"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: A6:62:3B:4B:2B:9A
          Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=73/100  Signal level:-174 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
The problem comes when I use ifconfig to configure the device ra0:

ifconfig ra0 192.168.2.1 && ifconfig netmask 255.255.255.0 && ifconfig broadcast 192.168.2.255

With this, when I type ifconfig appears:

ra0       Link encap:Ethernet  HWaddr 00:80:5A:22:E0:12
          inet addr:192.168.21.1  Bcast:192.168.21.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe22:e012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:720 (720.0 b)  TX bytes:13302 (12.9 KiB)
          Interrupt:10 Base address:0x8000

But I can't see tha computer with an other computer inside the same network. When y try  to do ping from other computer with ip 192.168.2.2 appears:

PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.
From 192.168.2.1 icmp_seq=1 Destination Host Unreachable
From 192.168.2.1 icmp_seq=2 Destination Host Unreachable
From 192.168.2.1 icmp_seq=3 Destination Host Unreachable
From 192.168.2.1 icmp_seq=5 Destination Host Unreachable
From 192.168.2.1 icmp_seq=6 Destination Host Unreachable
From 192.168.2.1 icmp_seq=7 Destination Host Unreachable

I thought that the problem was a card and I bought an other wireless card Conceptronic (C54Ri) but is the same.

I hope you can help me. Thank you

---

### Post by odin on 2005-08-02
[QUOTE=logan.bone]

ifconfig ra0 192.168.2.1 && ifconfig netmask 255.255.255.0 && ifconfig broadcast 192.168.2.255

With this, when I type ifconfig appears:

ra0       Link encap:Ethernet  HWaddr 00:80:5A:22:E0:12
          inet addr:192.168.21.1  Bcast:192.168.21.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe22:e012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:720 (720.0 b)  TX bytes:13302 (12.9 KiB)
          Interrupt:10 Base address:0x8000

[/QUOTE]

Either you posted wrong the ifconfig line or the display of ifconfig because I can see that your address is 192.168.**21** .1 instead of 192.168.**2** .1

---

### Post by logan.bone on 2005-08-02
Thank you odin that was an other configuration, but the problem was I had my PCI port wroken. When I changed wireless card an other port all was OK. :P
Thank you.

---

### Post by odin on 2005-08-02
happy you found the problem

 :grin:

---

