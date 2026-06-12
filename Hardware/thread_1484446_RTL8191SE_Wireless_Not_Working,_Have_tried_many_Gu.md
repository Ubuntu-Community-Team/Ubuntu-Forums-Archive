---
title: "RTL8191SE Wireless Not Working, Have tried many Guides"
date: 2010-05-15
forum: Hardware
---

### Post by nsteger123 on 2010-05-15
I cannot get my wireless to work. I have an RTL8191SE and i have installed the stock drivers, and they just don't work. Here's all my information:

```
[B]Wireless Info:
ifconfig[/B]
Code:
eth0      Link encap:Ethernet  HWaddr 00:26:6c:3a:c9:d7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe3a:c9d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63013145 (63.0 MB)  TX bytes:3977048 (3.9 MB)
          Interrupt:33 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32906688 (32.9 MB)  TX bytes:32906688 (32.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:a9:fd:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:ffffc90005088000-ffffc90005088100
```
```
[B]iwconfig
Code:[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Nothing shows up in the Hardware Drivers

---

### Post by nsteger123 on 2010-05-16
Bump

---

### Post by lidex on 2010-05-18
Use the make/model of this laptop to find the relevant page on this site:
[http://www.linlap.com/]("http://www.linlap.com/")

---

