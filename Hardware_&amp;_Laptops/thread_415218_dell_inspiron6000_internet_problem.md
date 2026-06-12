---
title: "dell inspiron6000 internet problem"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by buryan on 2007-04-20
i installed a fresh festy fawn yesterday but lost internet connection after the installation. it was working on ubuntu 6.10. 

here are some thing i found in logs;

Linux lagoongreen-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


lagoongreen@lagoongreen-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:22:EC:62:96  
          inet6 addr: 2002:a04b:72a9:5:214:22ff:feec:6296/64 Scope:Global
          inet6 addr: fec0::5:214:22ff:feec:6296/64 Scope:Site
          inet6 addr: fe80::214:22ff:feec:6296/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592735 (578.8 KiB)  TX bytes:10608 (10.3 KiB)
          Interrupt:19 

and here are dmesg.log and lspci-vvnn.log

---

### Post by buryan on 2007-04-20
here is dmesg.log

---

