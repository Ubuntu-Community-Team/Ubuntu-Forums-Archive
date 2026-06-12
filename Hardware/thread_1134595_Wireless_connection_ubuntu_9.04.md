---
title: "Wireless connection ubuntu 9.04"
date: 2009-04-23
forum: Hardware
---

### Post by kb2tfa on 2009-04-23
I just upgrade to 9.04. I've been using my wired conn, but now that new version supports wireless, I would like to use it.

I have a dell inspiron b120.

I activated the hardware driver, but still nothing.

when I check ifconfig I get no mac address. Is this right?


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by kb2tfa on 2009-04-23
a restart fixed it. wireless is working

apparently what i was seeing in the above was a loop back, and not the wireless card. after reboot, the card showed up

---

