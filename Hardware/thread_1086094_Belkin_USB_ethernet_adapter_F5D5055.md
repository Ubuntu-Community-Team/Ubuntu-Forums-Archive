---
title: "Belkin USB ethernet adapter F5D5055"
date: 2009-03-03
forum: Hardware
---

### Post by mscatdk on 2009-03-03
Hallo,

I'm trying to get a Belkin USB ethernet adapter to work, it looks like it is installed correct.

ethtool -i eth1:

driver: asix
version: 14-Jun-2006
firmware-version: ASIX AX88178 USB 2.0 Ethernet
bus-info: usb-0000:00:1d.7-7

lsusb:

Bus 005 Device 003: ID 050d:5055 Belkin Components F5D5055
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And it is shown as Eth1 in the network manager, but i would connect.
From the syslog I can see it is trying to receive IP address from DHCP but fail do to Time out. 

The adapter works fine under Windows XP.

I run Ubuntu 8.10, linux kernel 2.6.27-13.

Any help?

---

### Post by lars.thornqvist@pdahl.se on 2010-04-19
Did you find any solution to this? I have the exact same problem after upgrade to Ubunntu 9.10 :(

---

### Post by Q-Fireball on 2010-12-27
I have also the same problem! Ubuntu 10.10 won't work with this adapter although dmesg shows that the driver is loaded (asix) and eth1 shows up.

---

### Post by jwater7 on 2011-05-03
Same problem with debian kernel version 2.6.26-2.  Anyone have a resolution?

---

### Post by gssurya on 2011-05-30
Please tell me where I can find the driver for this product, Belkin, F5D5055 USB Gigabit ethernet adapter please.. My ethernet port is spoilt and I desperately want internet in my ubuntu..

---

### Post by umuro on 2011-06-28
In Natty 11.04, Belkin Gigabit USB 2.0 Adapter works out of the box...

---

