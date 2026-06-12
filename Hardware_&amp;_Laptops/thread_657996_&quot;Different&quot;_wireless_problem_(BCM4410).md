---
title: "&quot;Different&quot; wireless problem (BCM4410)"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by jkanounji on 2008-01-04
Hello everyone.

I'll jump straight to the point: 

I was just handed this new laptop at work, and of course, I refused installing Windows on it, so I formatted it and installed a fresh copy of Gutsy. The laptop is a Dell Inspiron 1300.
The wireless card built-in is a Broadcom (yay?) 4401.

The weird thing is, from day 1, I can see the wireless card if I do ifconfig, however, I can't set it to connect to anything, let it be roaming or specific ESSID.

I tried many options, from downloading the linux drivers from the official Broadcom website (what a joke), to using ndiswrapper.

I blacklisted BCM43xx

ndiswrapper looks fine, but it gives the strange feeling as if it "didn't do anything at all", and by that, I mean I still can see the card from ifconfig, but no luck connecting to anything.

If you would like some information about ndiswrapper,

> jkanounji@jkanounji-laptop:/etc/ndiswrapper$ ndiswrapper -l
b44win : driver installed
        device (14E4:170C) present (alternate driver: b44)

What's intriguing is the message from /var/log/messages and from dmesg, which states that:
eth1: link is not ready, 
> 
[ 5284.584000] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[ 5284.592000] usbcore: registered new interface driver ndiswrapper
[ 5760.080000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5830.692000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5844.300000] eth0: no IPv6 routers present
jkanounji@jkanounji-laptop:/etc/ndiswrapper$ 

And, needless to say, but I can't discover any wireless networks if I set the mode to roaming (from network manager)

Please, if anyone could help me, I'd really appreciate it, I'm about to bang my head to the wall

EDIT: Forgot to put what ifconfig displays:
> 
jkanounji@jkanounji-laptop:/etc/ndiswrapper$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:AC:F9:D3  
          inet addr:192.168.168.161  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feac:f9d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9110102 (8.6 MB)  TX bytes:2005459 (1.9 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:A9:7A:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 Memory:dfbfd000-dfbfdfff 

eth1:avah Link encap:Ethernet  HWaddr 00:16:6F:A9:7A:53  
          inet addr:169.254.6.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xa000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by jkanounji on 2008-01-08
No one? :(

---

### Post by jkanounji on 2008-01-09
/sigh

---

### Post by kvonb on 2008-01-09
-

---

### Post by kvonb on 2008-01-09
-

---

