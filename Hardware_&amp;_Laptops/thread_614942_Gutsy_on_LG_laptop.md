---
title: "Gutsy on LG laptop"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by kopolov on 2007-11-16
Hello,
I have recently installed Gutsy on my laptop.
LG laptop.
Model: F1
Processor: Intel core duo T2350
RAM: 2 GB
Wireless: Ralink rt73

I wish to report 2 consisting problems:
1. My wireless is not working at all.
It identifies the access point and the ESID but it shows a very low signal output (though it is located 1 meter from the access point).
I know for a fact that the wireless is working properly because there used to be Vista installation on this machine and the wireless worked flawlessly there, using WEP security.

2. Once the screensaver is activated (it is set to start after 10 minutes), it can go on OK for a time, and then the computer freezes completely. and I mean completely.
not only the gnome is not responding, mouse is not responding, keyboard is not responding, remote ssh is not allowed (though when the computer is not stuck, ssh is enabled and working).
The amount of time varies. It can be days, hours etc ... (usually at least few hours).
I also notices several times that the screensaver froze after a period of time (even though the screen is not set to go blank/hibernate/suspend at all) but at those moment I pressed a key/moved the mouse and the machine returned to the login/password screen (so it is ok).
But if I would not have done this, after a while, the machine would completely stuck.
Once it get stack, pressing ALT-CTRL-1/2/3/4/5/6 doesn't work either.

Thank you.

---

### Post by tinycamp on 2007-11-16
kopolov, could you post the output of lspci on your system?, are you using a 3D screensaver ???

cc

---

### Post by kopolov on 2007-11-18
lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
04:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
04:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
04:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

lsusb
Bus 005 Device 003: ID 0db0:6877 Micro Star International 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  


about the screensaver - I am using one of the screen savers which comes with Gutsy
"cyclone"

---

### Post by kopolov on 2007-11-20
I switched to another 2D screen saver "popsqaures" and up until now, the system did not got suck (yet)

---

### Post by kopolov on 2007-11-21
OK.
The 2D screensaver failed also.
It froze after more then 12 hours

---

