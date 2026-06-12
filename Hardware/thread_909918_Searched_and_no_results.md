---
title: "Searched and no results"
date: 2008-09-04
forum: Hardware
---

### Post by getnripped on 2008-09-04
I have ran a search, google (blackle), and ubuntu help file searched this issue. I have recently moved from AT&T DSL to Roadrunner. I have the same router that was working just fine with Ubuntu and AT&T. Now that I have changed to roadrunner I can't even access my router [http://192.168.0.1](http://192.168.0.1) I have tried many combinations with no success.

Running WRT54G Broadband Router v3 with motorola cable modem. When I run ifconfig:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:ad:ff:6d  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fead:ff6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:22071240 (21.0 MB)  TX bytes:3019895 (2.8 MB)
          Base address:0xb800 Memory:dfee0000-dff00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131759 (128.6 KB)  TX bytes:131759 (128.6 KB)

any thoughts?

---

### Post by cariboo on 2008-09-04
Try:

[http://192.168.1.1](http://192.168.1.1)

I have the same router and unless you have chnged the firmware the above ip address is the correct one. I have the same router, and I have it aliased in my /etc/hosts file as:

```
192.168.1.1 router
```

Jim

---

### Post by eggdeng on 2008-09-04
You and your router are on different subnets.
Go to System -> Administration -> Nework,  choose your device -> Properties. 
If your router is configured to use DHCP, then just choose the use dynamic IP option (Most likely).
If your router is not using DHCP, either change your IP to 192.168.2.102 or change your subnet mask to 255.255.0.0.

---

### Post by getnripped on 2008-09-14
Thank you all for the replies. I found there error was in my MAC address. It was still set for ADSL, I just had to enter my new MAC. Thanks again.

---

