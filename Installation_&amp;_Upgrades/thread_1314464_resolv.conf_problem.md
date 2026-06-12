---
title: "resolv.conf problem"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Picardy Beet on 2009-11-04
Hi,

I've got a strange problem at boot with my resolv.conf after upgrading.

My ISP is Orange, and to avoid a slow DNS resolution problem, I has to statically define my IP in /etc/network/interface. 
As resolv.conf is overwritten on every boot by resolconf,  dns-nameservers are also indicated in my interface configuration, like this :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 81.253.149.1 80.10.246.3

After a boot, everything on eth0 is correctly affected. But resolv.conf stays empty.
But this interface file is correct, and doing /etc/init.d/networking stop and start ensure the dns servers are correctly registered in resolv.conf.

Misconfiguration from my side? Bug?

---

