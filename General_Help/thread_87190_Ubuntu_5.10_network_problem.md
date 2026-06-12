---
title: "Ubuntu 5.10 network problem"
date: 2005-11-07
forum: General Help
---

### Post by Linuxuser on 2005-11-07
Please help. Just install Ubuntu 5.10 on Dell Inspiron 9300.

Broadcom 10/100 - eth0
Intel 2200 wireless - eth1

Problem 1 -

Ubuntu can talk to AP (D-Link DI-514), succesfully got a DHCP offer from DHCP however the DI-514 immediately release the IP offered. The confusing part is that I can ping from my Dell to other IP on the network, but they can't get back to me? I can't get on line.

How do I resolve this? 

Problem 2 -

Ubuntu can see my wireless interface, however, I can use Admin to get put in Key, it sucesssfully negotiated for DHCP IP but same problem occurs as described above. Also, my wireless indicator on the laptop is not lit up and I do not see any network icon on ETH1 interface on Ubuntu.

Much appreciate any comment on how to get these to work.

---

### Post by paddyg on 2005-11-07
have you checked Lease Time?

why don't you set a static ip for your box and turn DHCP off on the router?---I think you've got a router

Also, i had to add DNS servers manually to my Network settings to get online properly

---

### Post by Linuxuser on 2005-11-07
Paddyg,

Yes, my router (DI-514) is set to lease the IP on a weekly basis. Windows works perfectly OK.

The reason is that I do not want a static IP is because I move around a lot with different APs. So static IP is useless to me.

DNS name server? It is currently set to my ROUTER default (192.168.0.1).

---

### Post by Linuxuser on 2005-11-07
I have fixed the problem. 

However still can't get the wireless icon to display.

Any idea?

---

### Post by paddyg on 2005-11-08
[QUOTE=Linuxuser]I have fixed the problem. 
[/QUOTE]

i'm curious... what was wrong with your dhcp?

---

