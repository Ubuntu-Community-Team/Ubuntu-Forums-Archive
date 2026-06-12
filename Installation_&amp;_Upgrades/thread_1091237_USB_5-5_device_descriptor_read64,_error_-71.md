---
title: "USB 5-5: device descriptor read/64, error -71"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by aladin3 on 2009-03-09
At every boot of my Ubuntu 8.10 or 9.04a2, I get multiple errors related to USB ports, such as

[   20.234523] usb 5-5: device descriptor read/64, error -71
[   20.458418] usb 5-5: device descriptor read/64, error -71
[   20.682198] usb 5-5: new high speed USB device using ehci_hcd and address 6
[   21.099451] usb 5-5: device not accepting address 6, error -71
[   21.214292] usb 5-5: new high speed USB device using ehci_hcd and address 7
[   21.623103] usb 5-5: device not accepting address 7, error -71

and once at the login screen or after login gnome, mouse and keyboard are VERY slow.
The problem occurs since I added an analog TV tuner card
(Pinnacle PCTV Rave on PCI port). Before, Ubuntu ran fine.

The same machine runs fine with MS WinXP pro.

My config:
Athlon64 X2 4200
2Gb RAM
CG Radeon X800GT
1 HDD PATA
2 HDD SATA
1 HDD SCSI U2
2 HUBS USB on mobo
1 HUB USB on USB port
1 scanner USB
Mouse + keyboard USB
Dongle Wifi USB TPLINK
1 Pinnacle PCTV PCI
1 Creative SB 128 PCI
1 SCSI TEKRAM 390F PCI

Any help much appreciated!

Attached is my complete dmesg

---

### Post by aladin3 on 2009-03-16
Any idea?

---

### Post by magog45 on 2009-08-02
I have a similar error except the it is USB 5-7 and the error code is 110. I have an MSI P6NGM2 board intel 3.0 dual core 
Onboard control is Nvidia MCP73 series chipset based
Still reads usb devices but this is a new install so will continue to puzzle it out and post if I come up with something, searchs don't turn up anything

---

### Post by magog45 on 2009-08-02
Ok I was running windoze 7 on this machine and everything was fine but it was beta and expired. As to the USB error I noticed that my card reader wasn't working so I opened it up and moved the usb connecter from the the bottom row with only 4 pins to the top row with 5 pins(the yellow isn't used) and low and behold on my next boot the issue is gone. Not sure if that will help you but its worth a try.

---

### Post by aladin3 on 2009-08-03
my winXP pro runs also fine on my machine, and no error was mentioned in the devices manager, so I thought there is something wrong with the Linux USB drivers.

What are the two internal USB connectors labeled and good for?
perhaps the mobo user manual has this info.

---

### Post by dortmann on 2010-09-14
I just encountered this USB error on 10.04.  Simultaneously, my X would not boot.  I noticed "vga16fb" had somehow snuck into the system ... it was missing from etc modprobe.d framebuffer blacklist.

I after adding vga16fb to the blacklist file I have both X and usb functionality again.

DISABLE ALL FRAMEBUFFER MODULES.

lsmod | grep fb


Hope this helps.
[email]dortmann31415@yahoo.com[/email]

---

