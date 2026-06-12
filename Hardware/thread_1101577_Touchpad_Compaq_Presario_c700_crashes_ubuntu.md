---
title: "Touchpad Compaq Presario c700 crashes ubuntu"
date: 2009-03-20
forum: Hardware
---

### Post by kehon on 2009-03-20
It doesnt happen all the time but it happens often especially if i touch the touchpad too soon on my compaq presario c700 it will crash ubuntu the caps lock starts blinking and i have to hold power button for 15 seconds any ideas on how to fix cause its annoying 

also i just got wireless to work after messing with it is there another way

---

### Post by utnubuuser on 2009-03-20
Do you have gsynaptics installed?

Give people a bit clearer system info so they can see what your hardware setup is.
IE.  > lspci or  > dmesg in console.

---

### Post by kehon on 2009-03-22
how do i check i have not messed with mouse i just installed from cd and even live boot crashes sometimes so what ever is default is what i'm using also how do i get the internet working again did it once but i installed from usb and dont have cd to install or mess with packages i used last time

---

### Post by shantanubhadoria on 2009-04-25
I get the same issue and that too in a fresh install .I run a compaq presarion c700 (sub type is 770TU)

$lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


HTH
-Shantanu Bhadoria

---

