---
title: "firmware required"
date: 2012-03-25
forum: Hardware
---

### Post by david99world on 2012-03-25
Hi, basically I've just installed ubuntu and there's three things I'm sort of stuck with, first is it can't find drivers for my wireless card, ran lspci -nn and the results are below...

david@david-P5Q:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II Controller [11ab:6121] (rev b2)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

The second issue is it can only see one monitor with my asus560ti, and even then it appears to be as "unknown" - does anyone have drivers for this?

Finally, I think I might be a bit screwed with the last one but my sound card is a focusrite saffire6 usb, does anyone know if you can get drivers for this?

Apologies, if there's some fast way to find drivers I'm not aware of then sorry for wasting your time :)

---

### Post by Yellow Pasque on 2012-03-25
This should work for wireless:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

From searching, I don't see any drivers for the saffire card.

---

### Post by Mark Phelps on 2012-03-26
According to Google, that ASUS videocard is a rebranded GeForce GTX 560 card.  You should be seeing an option to install the Nvidia drivers for it.

---

