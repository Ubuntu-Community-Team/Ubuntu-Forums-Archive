---
title: "EDUP EP-MS8512 driver installation"
date: 2017-05-15
forum: Hardware
---

### Post by luiz-briganti on 2017-05-15
Good morning everyone, 
I'm trying to install my usb wifi adapter EDUP EP-MS8512 on Ubuntu 16.04. I thought the system would have installed it automathically, but it didn't. I tried different procedures that I found here on this forum, but they are old of 6-7 years and anyway didn't work. I managed to find the correct drivers on the web, but still I couldn't be able to install them. 
The "funny" thing is that if I type lsusb in my terminal, I get this

> luigi@Luigi-Ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


so the system seems to see the device, but still it doesn't work. It doesn't connect to wifi. Any hint or suggestion?

Thanks!

---

### Post by mörgæs on 2017-05-16
Hi, welcome to the fora.

Searching for drivers should not be necessary. First, have you connected to the internet using wired connection and installed all updates?

---

