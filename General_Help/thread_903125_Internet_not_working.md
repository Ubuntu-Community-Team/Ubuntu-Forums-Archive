---
title: "Internet not working"
date: 2008-08-28
forum: General Help
---

### Post by windriver on 2008-08-28
Hi

My internet has stopped working on my desktop (Hardy)after unplugging cable modem and router (Trendnet). However, it works fine without router on my laptop (WinXP). I have also tried without router on my desktop but nothing works. I have only one network card (eth0) enabled. Please help me out with this problem.

---

### Post by Crafty Kisses on 2008-08-28
Post the results of:
```
lshw -C network
```

---

### Post by rcrcomputing on 2008-08-28
> **windriver said:**
> Hi

My internet has stopped working on my desktop (Hardy)after unplugging cable modem and router (Trendnet). However, it works fine without router on my laptop (WinXP). I have also tried without router on my desktop but nothing works. I have only one network card (eth0) enabled. Please help me out with this problem.

Your laptop may work because you have the ppoe software from the dsl company to issue your name and password to connect. Have you tested the router at all?  Are you getting dhcp from the router?

---

### Post by windriver on 2008-08-28
> **rcrcomputing said:**
> Your laptop may work because you have the ppoe software from the dsl company to issue your name and password to connect. Have you tested the router at all?  Are you getting dhcp from the router?
I don't know exactly how to check router for dhcp; therefore, I have taken it out. Now I am trying for direct internet on Hardy with cable modem.

---

### Post by windriver on 2008-08-28
> **Codename said:**
> Post the results of:
```
lshw -C network
```
Got this message, Thanks 

*-network               
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:4c:69:6e:75:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=56 mingnt=8 module=tulip multicast=yes

---

