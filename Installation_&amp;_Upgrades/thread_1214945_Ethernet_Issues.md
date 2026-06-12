---
title: "Ethernet Issues"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by BryanA on 2009-07-16
Hey there. I just installed Ubunty 9.04 on an old Mac Mini PPC (no wireless) and can't for the life of me figure out the internet situation. Under network manager it shows:

Wired Network (Apple Computer UniNorth 2 GMAC (Sun GEM))
Wired Network (Realtek RTL8150 Fast Ethernet Adapter)

Both of these options are grayed out and I can't select either of them. The Realtek one is a usb ethernet deal.

Any help would be greatly appreciated. 

Thanks,
Bryan

[[IMG]http://imgur.com/8HiyLs.png[/IMG]]('http://imgur.com/8HiyL.png')

---

### Post by csabo2 on 2009-07-16
stupid question, must be asked: did you plug one in and try?

---

### Post by BryanA on 2009-07-16
Haha, yes I did and I made sure that the cable was working.

---

### Post by NullHead on 2009-07-16
Whats the output of the command "ifconfig -a"?

---

### Post by BryanA on 2009-07-16
eth0      Link encap:Ethernet  HWaddr 00:0d:93:60:a7:d0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xf800 

eth1      Link encap:Ethernet  HWaddr 00:10:60:e7:6c:98  
          inet6 addr: fe80::210:60ff:fee7:6c98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137350 (137.3 KB)  TX bytes:3204 (3.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr 12:e2:0d:50:0d:52  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[[IMG]http://imgur.com/8HiyLs.png[/IMG]]("http://imgur.com/8HiyL.png")

Screen shot

Thanks Again

---

### Post by NullHead on 2009-07-16
Try this: ```
sudo ifconfig up eth1
```

---

### Post by BryanA on 2009-07-16
It returns "eth1: Unknown Host"

Really appreciating the quick replies

---

### Post by BryanA on 2009-07-17
[SOLVED]

After turning off all power to the internet equipment for a while it fixed itself. 

Thanks again!

---

