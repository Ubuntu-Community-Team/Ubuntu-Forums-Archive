---
title: "Problems with Wireless network on my laptop"
date: 2009-11-17
forum: Hardware
---

### Post by MrDanielson on 2009-11-17
Hey people :)

I have installed Ubuntu 9.10 on my Laptop; An Acer Aspire 5040, old pc i know, but I can't get on the wireless network? Anybody that can help me? I have never tried to come on a wireless network with ubuntu, and i really need help :)

By the way, ubuntu 9.10 looks awesome :D I love it!  ;)

---

### Post by MrDanielson on 2009-11-17
BUMP:popcorn:

---

### Post by b&amp;m on 2009-11-17
First, run this command (Application>Accessories>Terminal) to get info on your wireless controller:

report-hw | grep controller

then,  try to install the proper driver (System>Administration>Hardware Drivers) for the controller.

---

### Post by MrDanielson on 2009-11-17
> **b&m said:**
> First, run this command (Application>Accessories>Terminal) to get info on your wireless controller:

report-hw | grep controller

then,  try to install the proper driver (System>Administration>Hardware Drivers) for the controller.
Uhm...

When i wrote report-hw | grep controller in terminal, it said command not found... 

And i Cant find any drivers in the hardware drivers thingy

---

### Post by b&amp;m on 2009-11-17
The command is "report-hw | grep controller".

This is my run:

salvatore@ubu:~$ report-hw | grep controller
lspci -knn: 00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
lspci -knn: 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
lspci -knn: 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
lspci -knn: 02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
lspci -knn: 09:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
salvatore@ubu:~$

---

### Post by MrDanielson on 2009-11-17
> **b&m said:**
> The command is "report-hw | grep controller".

This is my run:

salvatore@ubu:~$ report-hw | grep controller
lspci -knn: 00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
lspci -knn: 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
lspci -knn: 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
lspci -knn: 02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
lspci -knn: 09:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
salvatore@ubu:~$
Hey again :p

I tried using LAN network, then installed the updates and then the drivers - now it works :D!

---

