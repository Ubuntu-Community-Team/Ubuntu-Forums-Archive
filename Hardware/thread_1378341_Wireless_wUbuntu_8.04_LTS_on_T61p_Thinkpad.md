---
title: "Wireless w/Ubuntu 8.04 LTS on T61p Thinkpad?"
date: 2010-01-11
forum: Hardware
---

### Post by David.Davidian on 2010-01-11
Forum:

Need help in having Ubuntu set active my laptop's internal wireless connection. I don't need it to be automatic, I don't find commend lines, etc. I have 8.04 LTS installed because that is the only rev IBM Lotus Notes (IBM work laptop) supports. Normal intenral ethernet works (I am using it now). However, I must have missed something with regards to setting active the internal wireless hw. Yes, the wireless switch is turned on :-).

iwlist reports the wireless router, as well my neighbors:

dbd@Work-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for dbd: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:90:EE:B6:E0
                    ESSID:"3H9J2"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=-80 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000022d267d5e
          Cell 02 - Address: 00:18:01:E3:9B:39
                    ESSID:"1V3Y8"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/100  Signal level=-67 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004c1eb52798

ifconfig yields:

dbd@Work-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:86:54:d7:e9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:86ff:fe54:d7e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9739733 (9.2 MB)  TX bytes:4629338 (4.4 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160950 (157.1 KB)  TX bytes:160950 (157.1 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:9.76.73.106  P-t-P:9.76.73.106  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1362  Metric:1
          RX packets:10798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2761456 (2.6 MB)  TX bytes:1649506 (1.5 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.186.1  Bcast:172.16.186.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:15:0a:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-15-0A-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

(yes, I have VMware running XP in a VM, but it's powered off at this point)

What must one do to get this running? I have tried pulled the ethernet cable, etc. I would normaly use wired eithernet, but will be travelling a few weeks and will be stayng hotels that have wireless connections.


Thanks

---

### Post by David.Davidian on 2010-01-11
Solved --- Network Manager!

---

