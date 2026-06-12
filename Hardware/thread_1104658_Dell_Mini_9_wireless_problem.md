---
title: "Dell Mini 9 wireless problem"
date: 2009-03-23
forum: Hardware
---

### Post by frkingz on 2009-03-23
Hi,

Recently bought Dell Mini 9 with XP. Bought a new harddrive and installed Ubuntu 8.10. 

Everything worked great for about a week. Now no wireless. Wireless originally worked fine. Now it doesn't. Wired works fine.

Removed new harddrive, put in original with XP, wireless works fine.

Removed network-manager and replaced it with wicd, still no wireless.

Downloaded all updates including pre-release updates, no wireless.

Deleted Ubuntu, installed Xubuntu, no wireless.

Tried Kubuntu, no wireless.

Reinstalled Ubuntu, no wireless.

Tried everything else I could find on the internet, enabling broadcom drivers, FN+2 to turn on wireless, about twenty other things, still no wireless.

Any help appreciated. New to Linux but can usually figure things out myself with the help of Google. This is driving me nuts.

I have a feeling it is something simple and stupid. Something to do with eth1 and eth0 but I don't know enough about Linux to figure it out.

Thank you very much.

frk@hal9000d:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""

          Access Point: Not-Associated   

pan0      no wireless extensions.



frk@hal9000d:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:21:70:ca:48:ca  

          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::221:70ff:feca:48ca/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:12 errors:0 dropped:0 overruns:0 frame:0

          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2477 (2.4 KB)  TX bytes:7098 (7.0 KB)

          Interrupt:220 Base address:0x2000 



eth1      Link encap:Ethernet  HWaddr 00:1a:73:2d:9a:15  

          inet6 addr: fe80::21a:73ff:fe2d:9a15/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:80 errors:0 dropped:0 overruns:0 frame:0

          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)


frk@hal9000d:~$ sudo iwlist scan

[sudo] password for frk: 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :

          Cell 01 - Address: 00:1C:10:32:73:A0

                    ESSID:"linksys"

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:5/5  Signal level:-25 dBm  Noise level:-92 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s



pan0      Interface doesn't support scanning.

---

### Post by frkingz on 2009-03-24
Well I figured it out myself finally. Was ridiuclously simple.

Opened up Wicd preferences and in the Wireless interface box I placed eth1. Detected wireless netowrk and connected right up.

Strange though that reinstalling fresh copies of Ubuntu several times never solved the problem by itself. Anyone know if this is specific to the Dell Mini or is it a common problem?

Very frustrating for a new Ubuntu user like me.

---

