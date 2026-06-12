---
title: "Problems with wired and wireless networking after upgrade to hardy"
date: 2008-05-01
forum: Hardware
---

### Post by BobBenoit on 2008-05-01
Hello All,

I recently updated my laptop (Dell Inspiron 4150) from Gutsy to Hardy.  In the process something happend to my wired and wireless network interfaces. ifconfig gives the following output:

eth0      Link encap:Ethernet  HWaddr 00:08:74:48:83:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xcc00 

eth2      Link encap:Ethernet  HWaddr 00:08:74:46:71:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:708 (708.0 B)  TX bytes:708 (708.0 B)

while iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

when I open the network tools GUI, the configure option is greyed out so I am not able to configure any of the network interfaces.  On top of that, eth1 doesn't even show up there.

Everything worked fine when I was running Gutsy, I've been looking around for a while trying to see if anyone has had this problem, but haven't found anything.  Any help on this would be greatly appreciated!!

---

