---
title: "USB 3.0 port recognized by Linux as 2.0!"
date: 2015-08-30
forum: Hardware
---

### Post by popckorn on 2015-08-30
Hello, while trying to solve a problem with my SD card reader, I found this:

Output for lsusb with nothing plugged to the USB/SD ports:
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:07dc Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What I find unsettling is that I have 3 USB ports both of which are BLUE USB 3.0 ports, and the lsusb output says I have only one 3.0 port! Why is one of my 3.0 ports listed as 2.0?

This is my LSPCI output:
```
lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Unassigned class [ff00]: Device 1aea:6601

```

Thank you VERY much in advance, I hope I can bring my USB 3.0 port back from 2.0 and seize its power. Note I do have 3 ports, and only one is black, the other two are blue. Both the color of the port and the description of the laptop when I bought it confirm they are two USB 3.0 ports. 

Much obliged, wizards.

---

### Post by Yellow Pasque on 2015-08-30
A hub is not a port. Also, a hub does not necessarily have to have external ports (as the hub on Bus 2 is probably internal and used for your webcam and wireless devices). If you still don't understand, connect some devices and look at:
```
sudo lsusb -t
```
I'd also suggest running this once to update the human-readable names database for USB/PCI devices:
```
sudo update-usbids
sudo update-pciids
```

---

### Post by Yellow Pasque on 2015-08-30
Also, I noticed your card reader is having issues under Linux/Ubuntu: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1270676](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1270676)

---

### Post by popckorn on 2015-08-31
Thank you Temüjin! 

Both you and another user from Mint Forums have been kind enough to make me understand how a HUB can have several ports attached to it, and not all HUBS have an external port to which to connect.

I am learning fast thanks to you, guys (and gals)!

Have a great day and thank you for your prompt and clear answers!

---

