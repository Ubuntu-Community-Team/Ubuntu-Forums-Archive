---
title: "eth1 no detected after upgrade from 386 to genric kernel"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by Nick_milkman on 2007-03-08
Hi,

i am using an acer aspire 3273wxmi.

I am a bit of a newB on ubuntu, i originally started in dapper, then upgraded to edgy-386 kernel, i then realised the 386 kernel was not detecting my dual core so i upgraded this to a edgy-generic kernel.

The problem is since i upgraded to the generic kernel,my wireless card has disappeared, after working fine in the 386 kernel.

if i type, 
 lspci | grep Wireless

i get : 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

 and if i type ifconfig i get:

eth0      Link encap:Ethernet  HWaddr 00:16:36:A1:E0:E7  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fea1:e0e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4194975 (4.0 MiB)  TX bytes:1108956 (1.0 MiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
 
and finally when i type iwconfig
 i get :

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

so you can see my kernel is not detecting my eth1 connection, which is strange as my wireless never had any problems in edgy-386, and did not even have2 set it up.

i read that i needed to install the generic-restricted modules which i did, to no avial as my wireless card is still undetected.

Thank you for any help you can provide...!

---

### Post by jgcamp99 on 2007-03-08
Make sure the generic kernel is what you are booting into. I PXE'ed this notebook and 386 installed. Later I did what you did. I also made sure I installed Linux restricted modules. Mine runs well now, then again it's an L400 P3 700.

---

### Post by Nick_milkman on 2007-03-13
Hi thanks for your reply,

I am definatelly logging onto the generic kernel as i clearly choose the kernel on my grub loader, also if i logon back to my old 386 kernel my wireless option is there with no problems, so the problem is definattely with the generic kernel.

any other ideas..?

---

