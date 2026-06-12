---
title: "Start wifi on Aspire One after killswitch"
date: 2010-12-12
forum: Hardware
---

### Post by Melpomene on 2010-12-12
Hi, 

I accedently hit my wifi-killswitch button on the front of my Aspire One laptop. 
Now I do not seem to be able to restart it again. 

I seem unable to restart the network in the NetworkManager. 

I have tried to run ariodump-ng wlan0 but that only gives this output:

"SIOCSIFFLAGS failed: Operation not possible due to RF-kill. "

Is there anyway to restart the wifi?

Update:

**More outputs : **


** ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:1e:68:dc:ca:50  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fedc:ca50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:600779 (600.7 KB)  TX bytes:115350 (115.3 KB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118096 (118.0 KB)  TX bytes:118096 (118.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:04:d8:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by IcarusR on 2010-12-12
This may help

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html]("http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html")

---

### Post by Joe of loath on 2010-12-12
Have you tried jiggling the switch with the machine off and booting with it in the 'on' position?

---

### Post by Melpomene on 2010-12-12
That did it (the url). Up and running now :D

---

