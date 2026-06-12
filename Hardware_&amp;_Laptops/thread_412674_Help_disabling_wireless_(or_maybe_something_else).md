---
title: "Help disabling wireless (or maybe something else)"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by Ultravist on 2007-04-18
Today i took my laptop to work to show my friends how good is Ubuntu (no network there by the way so it was unplugged) and made myself a fool :( . The damn box booted extremely slowly with some firmware error(bcm43xx- which i've tracked it to the wireless card driver)..., hang on splashscreen about 3-4 minutes..every program runned very slowly (my opinions is that it kept searching for network). Any idea how to fix it? Or how to disable the wireless card and blacklist that damn bcm43xx in showing at startup (i can't disable the wireless card in BIOS because its not showing up? I paste here:

ultravist@ultravist-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:F5:65:B6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:3C:64:D2  
          inet addr:89.34.225.12  Bcast:89.34.225.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe3c:64d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12462718 (11.8 MiB)  TX bytes:866007 (845.7 KiB)
          Interrupt:50 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6548 (6.3 KiB)  TX bytes:6548 (6.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Even now as i write this if i unplug my network cable everthing slows down...every single aplication and i need to restart ubuntu with my cable inserted... I don't want wireless (frankly never erver used it) and please help me with the slow down after i unplug network cable. Please(i' m new to linux but wishing to learn).

---

