---
title: "Jaunty doesn't detect network device"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Sashin on 2009-04-19
I can't connect to the internet. With the live CD I could but after installing it doesn't detect any network device. I've tried with the live CD again and now even with it I can't use the internet.

---

### Post by StuartN on 2009-04-19
You need to know what kind of interface and hence which driver module should be loaded. List your attached interfaces by opening a terminal and typing "lspci" (if it is a card / motherboard) or "lsusb" if it is a USB adapter. Copy the output here, making sure your interface is in the listing you send.

---

### Post by trigoman05 on 2009-05-23
I have the same problem, I am currently using the live cd and my ubuntu partition does not recognize my network card. 

Here's my lspci output

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

I would like no note that I'm using Jaunty 9.04 64-bit. My laptop is an ASUS N80Vb and I am using WICD. The problem appeared after I restored my backup image.

Thank you.

---

### Post by GOfree on 2009-05-23
trigoman05,

Well, it looks like your system recognizes your card, at least. :)

You seem to have a Realtek ethernet card and an Intel wifi.

The problem is probably with your WICD configuration. I will have to look that up.

What does "ifconfig" give you? Have you tried "ifconfig <interface> up"?

Do you have gnome-network-manager?

---

### Post by trigoman05 on 2009-05-23
Actually I got it working now, WICD had my default wireless interface as wlan0 and my wired interface as eth0, when in reality it is wlan1 and eth1. I discovered this by going to the terminal and typing ```
iwspy
``` then I got this output 
```
lo        Interface doesn't support wireless statistic collection
eth1      Interface doesn't support wireless statistic collection
wmaster0  Interface doesn't support wireless statistic collection
wlan1     Interface doesn't support wireless statistic collection
```

This is how I realize my connection was not being used.
Thanks :D, it was a lot simpler than I thought

---

### Post by GOfree on 2009-05-23
Your wicd configuration should be in /etc/wicd/manager-settings.conf (from what I have read).

Can we have a look at that?

(I haven't used wicd, so I may not the best person to ask, but I do use netcfg and the principles should be similar.)

---

### Post by GOfree on 2009-05-23
great!

nice work!

see you :)

---

