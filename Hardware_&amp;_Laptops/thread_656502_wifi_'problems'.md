---
title: "wifi 'problems'"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by aorthr33 on 2008-01-02
I'm running Gutsy on a new Vostro 1400 (dell), but I just started having a problem with the wifi.  Admitedly, I'm doing some non-standard things.  The laptop came with the Broadcomm mini-pcie wireless card (4311), and I was able to get it working with the restricted drivers- no big problems.

Today, I installed another wireless card (another pcie - this time an Intel 3945ABG card).

Both cards worked fine for a while, and I was testing both cards with kismet - again, all is fine.  I logged out to switch from Gnome to Xfce, and now the original (eth1 - broadcomm 4311) card has dissappeared.  It is not listed in ifconfig, and I can't issue the 'up' command.  When I launch NetworkManager, the card is displayed, but I can't do anything to activate it.  The second card (eth2 - 3945ABG) seems to be working fine.

lspci gives the following 

```
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

Any ideas?

---

### Post by jazzgossen on 2008-01-03
> **aorthr33 said:**
>  now the original (eth1 - broadcomm 4311) card has dissappeared.  It is not listed in ifconfig, and I can't issue the 'up' command.  


What happens when you do "sudo ifup eth1"? Any error messages?

---

### Post by aorthr33 on 2008-01-03
I hate self resolving problems.  I shut my laptop down last night, and when I rebooted to try the ifup command from jazz, everything seems back to normal.


```
trey@Samson:~/wifi/kismet logs$ sudo ifup eth1
[sudo] password for trey:
Sorry, try again.
[sudo] password for trey:
ifup: interface eth1 already configured
trey@Samson:~/wifi/kismet logs$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:F9:1E:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1E:4C:52:C0:B6  
          inet addr:192.168.200.102  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe52:c0b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4286 errors:0 dropped:833 overruns:0 frame:0
          TX packets:3883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3849917 (3.6 MB)  TX bytes:666435 (650.8 KB)
          Interrupt:10 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr 00:18:DE:63:20:67  
          inet addr:192.168.200.103  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe63:2067/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3773 errors:0 dropped:224 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3822649 (3.6 MB)  TX bytes:4124 (4.0 KB)
          Interrupt:16 Base address:0x2000 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:F9:1E:18  
          inet addr:169.254.4.62  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```



If it goes haywire again, I'll try to revive this thread.   thanks.

---

