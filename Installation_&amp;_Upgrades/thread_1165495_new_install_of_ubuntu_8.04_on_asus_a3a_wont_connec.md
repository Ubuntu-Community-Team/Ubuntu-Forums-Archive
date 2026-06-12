---
title: "new install of ubuntu 8.04 on asus a3a wont connect to internet"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by V8pedals on 2009-05-20
Having trouble connecting to internet via router tp-link Model td-8840
it worked fine under 7.04.  
It has worked once then I let it update then stopped working next time I rebooted. 
Wired connection is set to dhcp
 #lspci rtl8139/810x is listed

checked most things listed below

grant@grant-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:ab:d5:67  
          inet6 addr: fe80::215:f2ff:feab:d567/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 00:15:f2:ab:d5:67  
          inet addr:169.254.9.82  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118986 (116.1 KB)  TX bytes:118986 (116.1 KB)

(#/var/run/network/IFSTATE)

lo=lo
eth0=eth0

(#etc/network/INTERFACES)

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

grant@grant-laptop:~$ cat /var/log/dmesg|grep -i eth0
[   26.326854] eth0: RealTek RTL8139 at 0xd800, 00:15:f2:ab:d5:67, IRQ 21
[   26.326857] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   32.336489] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.160041] NETDEV WATCHDOG: eth0: transmit timed out
[   37.273957] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   37.273962] eth0: Tx queue start entry 4  dirty entry 0.
[   37.273965] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   37.273969] eth0:  Tx descriptor 1 is 00082156.
[   37.273972] eth0:  Tx descriptor 2 is 00082156.
[   37.273975] eth0:  Tx descriptor 3 is 00082156.
[   37.273997] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.931554] NETDEV WATCHDOG: eth0: transmit timed out
[   38.023190] eth0: no IPv6 routers present
[   38.172111] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   38.172115] eth0: Tx queue start entry 4  dirty entry 0.
[   38.172119] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   38.172122] eth0:  Tx descriptor 1 is 0008203c.
[   38.172125] eth0:  Tx descriptor 2 is 0008203c.
[   38.172128] eth0:  Tx descriptor 3 is 0008203c.
[   38.172150] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   39.106862] NETDEV WATCHDOG: eth0: transmit timed out
[   39.333077] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   39.333081] eth0: Tx queue start entry 4  dirty entry 0.
[   39.333085] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   39.333088] eth0:  Tx descriptor 1 is 0008205a.
[   39.333091] eth0:  Tx descriptor 2 is 0008203c.
[   39.333094] eth0:  Tx descriptor 3 is 0008204e.
[   39.333116] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
grant@grant-laptop:~$

---

