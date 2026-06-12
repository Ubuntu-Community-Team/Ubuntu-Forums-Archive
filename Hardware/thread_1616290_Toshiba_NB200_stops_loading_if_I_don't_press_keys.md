---
title: "Toshiba NB200 stops loading if I don't press keys"
date: 2010-11-08
forum: Hardware
---

### Post by samuelalexdev on 2010-11-08
Hi guys,
I'm really frustrated with this I tried all versions of ubuntu..
So my laptop stops loading if I don't press keys or move the touchpad.
This happens while booting,playing media,sometimes even if I don't do nothing (my clock goes back with some minutes) and while shutting down.
Tell me what information you need and I'll give it to you.
I really need to solve this issue ubuntu is my favourite distro I tried them all.
I searched a lot and didn't find anything about this.
My sata controller is set to Compatibility(not AHCI).
The netbook is NB200(NB205 US),Intel Atom N270
It has the intel 945GMA graphics chip

Edit // Here is some more info 

**lspci** : 


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

**uname -r ** :

2.6.35-22-generic

And at the moment I'm using the latest updated kubuntu,but as I mationed it happens with all variants

---

### Post by samuelalexdev on 2010-11-08
Anyone?

---

### Post by samuelalexdev on 2010-11-09
Since nobody answered for the guys who are having the same issue they might try this it's a workaround that worked for me I can't know if it's ok for you.

This is what didn't work for me :
1 Disabling IPv6
2 Adding tsched=0 after 'load-module module-udev-detect' in /etc/pulse/default.pa (it made problem less notable,but media playing was a horror)

After playing for hours I went in the BIOS changed the processor power settings
to always low(not dynamic) and guess what it worked :D now it's true that I lost the power management but at least I have a usable ubuntu..
I'm sure the guys will fix this there is a bug report open on launch pad
HERE --> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/661327]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/661327")

---

### Post by samuelalexdev on 2010-11-12
updated to 2.6.37-020637rc1-generic
everything works like a charm now :popcorn:

---

### Post by Axellink on 2010-11-22
Where do you get the update from mate?

---

