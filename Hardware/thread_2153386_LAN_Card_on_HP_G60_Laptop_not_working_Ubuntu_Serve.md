---
title: "LAN Card on HP G60 Laptop not working Ubuntu Server 12.10"
date: 2013-06-10
forum: Hardware
---

### Post by BmanTheBoss on 2013-06-10
Haiee, so on my one laptop (HP G60), the wifi is not working (or more specifically, not detected). I ran lshw -C network and it only showed up my eth0 port, and it was disabled. I believe I have the LAN card hooked up correctly, but even when I tried many ways of hooking it up, none of them worked. I have been experimenting quite a bit, but haven't found anything. I hope someone can help me.

---

### Post by BmanTheBoss on 2013-06-11
Now, I have the computer directly hooked up to my router, but it can't install any packages. I ran ifconfig, and no ipv4 or anything comes up.

---

### Post by steeldriver on 2013-06-11
What are the contents of your /etc/network/interfaces file? 

Did you get a valid network connection during the installation process? Maybe the ethernet interface is disabled in BIOS?

---

### Post by BmanTheBoss on 2013-06-12
interfaces says:

"This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces(5).
The loopback network interface
auto lo
iface lo inet loopback"

I did not get a valid connection during installation because of something involving dhcp. Also, every time I try to access the BIOS, it takes me straight to the GRUB menu.

---

### Post by steeldriver on 2013-06-12
Well on the Server version, you won't get a wired LAN connection unless you have a definition for it (in addition to the lo definition) in the /etc/network/interfaces file - *IF* you are connecting to a router that acts as a DHCP server for your LAN, then that might be as simple as 

```

auto eth0
iface eth0 inet dhcp

```
or
```

auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.1.1

```

(replace 192.168.1.1 by your router's IP address if you router is acting as a forwarding nameserver, or you can put a public DNS server (or serveral) in there e.g. Google's 8.8.8.8, 8.8.4.4 or the equivalent from OpenDNS) - see [http://wiki.debian.org/NetworkConfiguration#Configuring_the_interface_manually](http://wiki.debian.org/NetworkConfiguration#Configuring_the_interface_manually) for more general info including static IP setup

Hope this helps

---

### Post by BmanTheBoss on 2013-06-20
I just found out that I didn't even have the LAN card plugged into the motherboard :P It works now.

---

