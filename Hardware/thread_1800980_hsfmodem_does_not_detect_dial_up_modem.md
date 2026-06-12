---
title: "hsfmodem does not detect dial up modem"
date: 2011-07-09
forum: Hardware
---

### Post by rock_rebel on 2011-07-09
Hi,

I'm currently running Ubuntu 11.04 on my IBM Thinkpad T60. The Kernel version is 2.6.38-8-generic. I've installed the generic drivers from the linuxant website, but the driver doesn't detect that there's a modem installed. The modem works fine in Windows. I went through an extensive guide found in another thread, but this didn't solve the issue. I'm now noticing that after I restarted my sound driver disappeared and now there's no sound. I'm really frustrated with this because I would really like for the modem to work, in case I ever need to use it where wireless isn't available. Has anyone gotten the modem to work on the Thinkpad T60? 

Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

lsusb: 

Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks!

---

### Post by foresthill on 2011-07-10
Linuxant is a joke. And for the price that you pay for one of their proprietary drivers, you can buy an external serial modem that will be much faster and more reliable than any software-based modem using their driver.

I see used serial modems all the time at thrift stores for around $5 or less.

If you're using a laptop that doesn't have a serial port, you can get a serial to USB adapter for very cheap that will fix this problem. There are also USB-based modems, by they can be almost as problematic as software-based Winmodems like the one you're using.

Anyone who has been through the unfortunate saga of trying to get a Winmodem to work in Linux generally will tell you that serial modems are the way to go if you're using dial-up. They're basically plug and play.

---

### Post by rock_rebel on 2011-07-10
Thanks for the info! I'll search for a serial modem rather than spending hours trying to get this thing to work. Would Ubuntu detect a PC card slot modem? I've seen a few of those on Ebay going for pretty cheap. All old technology. Broadband should be available everywhere, but sadly if there's no money to be made on high speed subscriptions in an area, that area will always have dial up.

---

