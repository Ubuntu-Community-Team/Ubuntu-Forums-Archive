---
title: "Asus X550LD unable to connect to wired network, Atheros AR9565"
date: 2014-07-05
forum: Hardware
---

### Post by Manoj Kumar on 2014-07-05
Hi,

I bought a Asus X550Ld and I'm regretting it since the day I bought it, my recent trouble being that my laptop is unable to connect to the LAN, The ethernet connection, disconnects before the laptop is able to connect. I'm sure the port works fine.

I did 

```
lspci -vv | grep Atheros
```

to find out that this is the output

```
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

My wifi works really well.
I saw questions like these, [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller) and I've tried out the solutions but something or the other seems to fail.

Any suggestions would be highly appreciated, since a majority of my work depends on if I'm able to connect to the LAN or not.

---

### Post by Manoj Kumar on 2014-07-05
I've fixed this issue by compiling from backports,

1. Do 

```

uname -r

```

2. check out the backports version compatible and then

```

make defconfig-alx
make -j4

```

3. Reboot

Works like a charm.

---

