---
title: "ifconfig gives weired 'dropped:' count"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2009-01-18
I've installed 8.10 32 bit on a system with Gigabyte G45M-DS2H
motherboard. Networking works without apparent problems.

When looking at the ifconfig out however I get
[INDENT]
  eth0  Link encap:Ethernet  ...
[INDENT]
        RX packets:779195 errors:0 dropped:1846567167 overruns:0 frame:0
        TX packets:429104 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000 
        RX bytes:1170354271 (1.1 GB)  TX bytes:29663754 (29.6 MB)
        Interrupt:221 Base address:0x4000 
[/INDENT]
[/INDENT]
The dropped counter is very quickly increasing when data is
transfered, reaches 2^32, wraps and starts all over. The number
is obviously wrong.

Has anybody seen this behavior before ?
Any help/hint is very welcome.

---

### Post by wfjm on 2009-02-08
This problem disappeared after upgrading to kernel kernel 2.6.27-11.
I didn't check, but I have to assume that there was a driver fix.

---

