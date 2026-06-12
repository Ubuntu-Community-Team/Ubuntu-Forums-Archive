---
title: "how to install network card on ubuntu!?"
date: 2010-03-17
forum: Hardware
---

### Post by addernator on 2010-03-17
Hey guys i recently installed ubuntu 9.10 on my pc with my network card already plugged in however when it first ran i saw it had not installed it and it says there are no network devices available, when i was running windows xp on the machine before it was fine, i am somewhat at a loss because i cannot do anything with the machine without internet it is useless to me.
Is there anyway i can install the network card manually?

Thanks, Adam.

---

### Post by tr333 on 2010-03-17
Try the following commands in a terminal:

```
ifconfig -a
```
This will show all available network interfaces on the computer.  Eg.  "eth0" for ethernet, "lo" for loopback, "wlan0" for wifi.

If that doesn't show your ethernet connection, then try:

```
sudo lspci -vvnn
```
That will list all PCI devices on the system (including Ethernet).

```
sudo lshw
```
This will list all the hardware in your computer (easier to understand the output than lspci).

If the ethernet doesn't appear in any of this output then the OS isn't seeing the network card.

---

