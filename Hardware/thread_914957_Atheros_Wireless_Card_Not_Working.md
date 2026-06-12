---
title: "Atheros Wireless Card Not Working"
date: 2008-09-09
forum: Hardware
---

### Post by oxsyn on 2008-09-09
Just did a fresh install of Ubuntu 8.04 64bit Desktop on my Asus M70Vm-X1.  The wireless card has an atheros chipset.  If I plug in my Realtek USB wireless card, the wifi drivers kick in and the wlan0 device becomes active (the USB card).

So here's some more info:

> f4rr4r@Neutron:~$ lspci
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
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
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0648 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
f4rr4r@Neutron:~$ 


You can see the Atheros Ethernet Controller shows as an "Unknown Device."

I don't see anything in dmesg about the atheros wireless card.

And obviously, it doesn't show up in ifconfig.

I'd really, really, really like to get this card working with the madwifi drivers rather than using ndiswrapper if possible.

---

### Post by dabl on 2008-09-09
It's not good that the model of the Atheros wireless controller is not detected -- that may be fatal to getting it working.

On sidux (a Debian linux) on my Eee PC 4G, I can (a) clean out the madwifi stuff and (b) install the new ath5k driver on my Atheros chip with the following two commands:

```
sudo apt-get purge madwifi-tools
modprobe ath5k
```

prolly worth a try.

---

### Post by jestemradek on 2008-09-25
Hello

please update pciid

```
sudo update-pciids
```

after update lspci shows:
```
03:00.0 Network controller: Intel Corporation Device 4232

```

This is Intel Wifi Link 5100

In kernel 2.6.27 you have drivers implemented ;-)

Don't forget - you must install firmware iwl5000

Good luck

---

### Post by Mgiacchetti on 2008-09-25
> **jestemradek said:**
> Hello

please update pciid

```
sudo update-pciids
```after update lspci shows:
```
03:00.0 Network controller: Intel Corporation Device 4232

```This is Intel Wifi Link 5100

In kernel 2.6.27 you have drivers implemented ;-)

Don't forget - you must install firmware iwl5000

Good luck

interesting, cause after updating to intrepid I cannot use my wifi at all.

(intrepid comes with the 2.6.27 kernel ;) so there are more problems with this than you may think.  I've personally tried everything.

Also, does anyone know how to shut that stupid ambient light sensor off while in ubuntu?

[B][COLOR=Red]****update**** 
```

sudo su
enter password
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

```
[/COLOR][/B]
(ASUS m70vm-x1)

Also to the OP 
If we can find a way to pull the drivers from the express gate linux installed on this thing we may be in business.

---

### Post by Mgiacchetti on 2008-09-26
Default install, do this...
```

sudo su
enter your password
echo 0 > /sys/devices/platform/asus-laptop/bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan

```

---

