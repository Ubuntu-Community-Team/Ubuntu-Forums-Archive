---
title: "Acerf Aspire 5680 WLMI disappointment"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by atasaRossios on 2006-12-11
](*,)
Hello everyone,
I was very much disappointed when installed edgy on my new Aspire 5680 WLMI.
My Ethernet card which is a Broadcom NetLink Gigabit refuses to connect to my lan and Internet.
It uses tg3 driver which modprobe says is loaded.
I haven't test the wireless but it seems is OK its a Intel Pro....

My /etc/network/interfaces 

auto lo
iface lo inet loopback

> auto eth0
iface eth0 inet dhcp

which I made it now 

> auto lo
iface lo inet loopback

iface eth0 inet static
address 192.68.2.40
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0

iface eth1 inet dhcp
wireless-essid FOG
wireless-key test
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1


just in case it was the dhcp thing confusing the system but no luck.

During installation also when comes to configure the network with dhcp, i got a message that could not find the gateway.

I do have another desktop computer with edgy installed and works fine via dhcp.
The dhcp and name server for my home lan is a dapper drake pc and the gateway is the adsl router.
Any comment or help very much appreciated. 
I also have questions if anyone got his card reader, the onboard camera and hibernation working.
Is a Centrino Duo machine and /proc/cpuinfo shows only 1 processor
 
Is that all to much asking for a linux distribution?
Thanx

---

### Post by atasaRossios on 2006-12-11
Core Duo shows 2 proccecors with generic kernel OK
But Suspend and Hybernate not working

---

