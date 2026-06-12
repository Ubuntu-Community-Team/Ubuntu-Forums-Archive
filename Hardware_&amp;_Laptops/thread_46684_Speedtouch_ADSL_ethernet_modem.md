---
title: "Speedtouch ADSL ethernet modem"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by PaulWiggers on 2005-07-05
Hello,

A few days ago I have installed Ubuntu. Up till now I cannot make the modem work. In windows all works fine, but in Ubuntu I can't even ping my modem. It gives me the messages "Network unreachable"

My network card is installed and I think that he is working properly.
I have an external ADSL modem. A Thomson Speedtouch 510 who is connected with my computer through an ethernet cable, so no usb.

Does anyone have a sollution for this?

TIA

Paul

---

### Post by PaulWiggers on 2005-07-06
I still need help with this. Please help me solve this problem, right now i am not using ubuntu at all because of this problem.

---

### Post by PaulWiggers on 2005-07-07
here is the ifconf output hopefully this will give more information on the problem

eth0      Link encap:Ethernet  HWaddr 00:0B:6A:1A:FF:BA
          inet6 addr: fe80::20b:6aff:fe1a:ffba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:10910 (10.6 KiB)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15560 (15.1 KiB)  TX bytes:15560 (15.1 KiB)

---

