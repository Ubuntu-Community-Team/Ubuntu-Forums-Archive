---
title: "ubuntu on packard bell ME35 ; problem with wireless"
date: 2009-12-27
forum: Hardware
---

### Post by ubumasi on 2009-12-27
Hi all,

I'm new to ubuntu. I have installed ubuntu 9.10 on packard bell ME35 laptop. It seems that everything is working except my wireless card and that's annoying.

Wireless card is realtek 8187b:
0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

I have tried everything before posting to this forum, I have even tried with ndiswrapper as it use to work in archlinux, but I can't get it to work.

It seems that card is up and scans networks because I can see the list of available networks.

The problem is that it tries to connect, asks for wep key(64bit hex) and then it takes up to 2-3 minutes where it's trying to connect, and then it asks again for key, and so on.

Unable to connect.

Any help is appreciated. Thanks in advance.

---

### Post by ubumasi on 2009-12-31
Ok, I got this working by reinstalling the NetworkManager and using native driver rtl8187

But now I have another problem, everytime I boot I have to load native driver rtl8187 manually: modprobe rtl8187

if I put this in /etc/modules it will load the driver but I'm unable to connect to network, because 

I want to load driver somewhere in late boot, how can I do that?

---

