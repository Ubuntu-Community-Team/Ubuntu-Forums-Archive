---
title: "tcp\ip connection"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by gabriel.pelmus on 2007-11-21
hello. i have a problem with my internet connection on ubuntu 7.10. my laptop connects to the internet through a network. the problem is that i have to set my ip:192.168.7.24, subnetmask:255.255.0.0,gateway:192.168.3.1 and dns:192.168.3.1. i also have to modify my mac address because the net is blocked on the address of an older computer and i can't find the network administrator to talk to him.the new mac address shoul be 00-30-84-40-90-d0. can anyone help me please?

---

### Post by nick_h on 2007-11-21
You need to edit your /etc/network/interfaces file.

For the manual page, type:
```
man interfaces
```

---

### Post by sisco311 on 2007-11-21
> **gabriel.pelmus said:**
> hello. i have a problem with my internet connection on ubuntu 7.10. my laptop connects to the internet through a network. the problem is that i have to set my ip:192.168.7.24, subnetmask:255.255.0.0,gateway:192.168.3.1 and dns:192.168.3.1. i also have to modify my mac address because the net is blocked on the address of an older computer and i can't find the network administrator to talk to him.the new mac address shoul be 00-30-84-40-90-d0. can anyone help me please?

edit your /etc/network/interfaces file
```
gksudo gedit /etc/network/interfaces
```you need something like this:
> auto eth0
iface eth0 inet static
  hwaddress ether 00:30:84:40:90:d0
  address 192.168.7.24
  netmask 255.255.255.0
  gateway 192.168.3.1
  dns-nameserver 192.168.3.1

---

### Post by gabriel.pelmus on 2007-11-22
i made those changes in the interfaces file but i still don't have an running internet connection.:(

---

### Post by nick_h on 2007-11-22
If you just cut and paste from sisco311's post then check the netmask.

You can check the settings by typing:
```
ifconfig
```

Try starting the interface from the terminal using ifup and see what messages you get.

---

