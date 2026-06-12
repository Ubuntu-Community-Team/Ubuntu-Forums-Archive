---
title: "BCM4303 and fwcutter on 7.10 gusty."
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by tomasz1 on 2007-11-22
Hello all.
 
First, sorry for my english.
 
I have a HP Pavillion zv5000 and I have just installed Ubuntu 7.10 Gusty for Amd 64.
 
I am using fwcutter to configure the wireless card BCM4303 from Broadcom.
 
It seems that all is correcto but It doesn't work. When I try to ping my router, the result is"host unreachable".

Versions installed:

   bcm43xx-fwcutter_20060108-6buildlamd.deb
   wl_apsta-3.130.20.0
   Also I try with bcmwl5.sys

But the result ever it's the same.

Could you help me?

 
Here below I put the result of several commands:
 
 
**root@Tomi:/var/log# iwconfig eth1**
eth1 IEEE 802.11b ESSID:"Sapietin" Nickname:"Broadcom 4301" 
Mode:Managed Frequency=2.462 GHz Access Point: 00:A0:C5:12:90:EE 
RTS thr:off Fragment thr:off 
Encryption key:7969-672E-6C65-6E67-2E63-616C-69 Security mode:open 
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 
 
 
**root@Tomi:/var/log# ifconfig eth1**
eth1 Link encap:Ethernet HWaddr 00:90:4B:57:C0:8B 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0 
DIFUSIÓN MULTICAST MTU:1500 Metric:1 
RX packets:34 errors:0 dropped:2 overruns:0 frame:0 
TX packets:151 errors:0 dropped:0 overruns:0 carrier:0 
colisiones:0 txqueuelen:1000 
RX bytes:4010 (3.9 KB) TX bytes:9895785 (9.4 MB) 
Interrupt:17 Base address:0x8000 
 
 
**root@Tomi:~# iwlist scan**
lo Interface doesn't support scanning. 
 
eth0 Interface doesn't support scanning. 
 
eth1 Scan completed : 
Cell 01 - Address: 00:A0:C5:12:90:EE 
ESSID:"Sapietin" 
Protocol:IEEE 802.11b 
Mode:Master 
Channel:11 
Frequency:2.462 GHz (Channel 11) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
Quality=84/100 Signal level=-52 dBm Noise level=-46 dBm 
Extra: Last beacon: 8ms ago 
 
 
**root@Tomi:~# netstat -rn**
Kernel IP routing table 
Destination Gateway Genmask Flags MSS Window irtt Iface 
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1 
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth1 
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth1

---

