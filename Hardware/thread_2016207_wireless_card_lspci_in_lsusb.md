---
title: "wireless card lspci in lsusb"
date: 2012-07-04
forum: Hardware
---

### Post by mut3d87 on 2012-07-04
hi everyone i have been having this problem upgrading my wireless card and found out that my original wireless card (rtl8187b) shows up as lsusb and not in lspci. My new card (Pegatron UPWL6025) is not showing up in either and im stuck with ideas please help.Im currently running debian testing i know it not ubuntu but ive found this forum more helpful in the past and the debian forum i posted to haven't even  responded please help.

my laptop toshiba equium a200-1v0
my original wireless card readout with lsusb

```
muted@debian:~$ lsusb

Bus 003 Device 005: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
```

and my output with my broadcom mini-pci wireless n card staright out of a virginrouter vwmg480 which i found out wass in there straight from [***HERE***]("http://cdkr.co.uk/projects/computers/virgin_VMDG280/")

as from what ican see it doesnt show up.

lspci

```
muted@debian:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
```

lsusb

```
muted@debian:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 062a:0102 Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9170+AR9101]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

as you can see it is not being registered at all. When i switched over to windows to see if i can install it any easier on there the device maanger had an unkown device but any of the drivers i pointed it to wouldnt work. Anyone know of a solution?

dmesg doesnt even show the mini-pci card being inserted

---

### Post by mut3d87 on 2012-07-05
bump 

Is it reasonable to bump after 24hrs?

---

### Post by ahallubuntu on 2012-07-05
Perhaps this wireless card is not compatible with your laptop?  Just because you can plug it in does not mean it will work.

How did you decide to buy this specific card for your Toshiba?

The card itself might be bad or not plugged in correctly.

I'd personally stick with Intel wireless cards for Linux, for software reasons: they seem to have the best in-kernel support.  I see that one version of the A200 used an Intel 3945ABG card:

[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&BV_UseBVCookie=yes&PRODUCT_ID=128463](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&BV_UseBVCookie=yes&PRODUCT_ID=128463)

A guess (not a guarantee) is that the Intel WiFi Link 5100 AGN card will work in this laptop; I have installed it in several different laptops successfully, including an old Dell that came with a 3945ABG card.

---

### Post by mut3d87 on 2012-07-10
hi thanks for the reply im thinking the same thing maybe a bios whitelist which is a fair bit of hardwork but i already unlocked toshiba's bios to lower the thermal trips so maybe i can find where it is located

---

### Post by ahallubuntu on 2012-07-10
I've never seen a Toshiba with a BIOS white list for wireless cards.  In any case, the computers I have seen (HP, Lenovo laptops) with white list will warn you about the card during POST and not even allow you to continue until you power off and remove the unapproved card.

It's more likely the card is simply not compatible with your laptop.  I'm not sure why you seem to think this couldn't be the case.  Not any card you plug in is guaranteed to be hardware compatible.

---

