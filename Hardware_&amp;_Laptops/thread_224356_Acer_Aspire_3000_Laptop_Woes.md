---
title: "Acer Aspire 3000 Laptop Woes"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by Raistlin355 on 2006-07-27
Does anyone know how to keep the wireless card on at bootup so you don't have to boot into Windows to get it working? Basically whats happening is my wireless won't work unless I first boot into windows and connect and then boot into Ubuntu and it'll connect just fine but it's annoying as crap to have to rely on windows for this one function.

---

### Post by costoa on 2006-07-27
> **Raistlin355 said:**
> Does anyone know how to keep the wireless card on at bootup so you don't have to boot into Windows to get it working? Basically whats happening is my wireless won't work unless I first boot into windows and connect and then boot into Ubuntu and it'll connect just fine but it's annoying as crap to have to rely on windows for this one function.

The answer is in /etc/network/interfaces (something like "auto eth1").  Could you please post a copy ("X"ing out any keys)?

---

### Post by Raistlin355 on 2006-07-28
Here you go:

auto lo
iface lo inet loopback

#iface eth1 inet dhcp
#wireless-essid xxxx
#wireless-key s:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

#auto eth1

#iface eth0 inet dhcp

#auto eth0

---

