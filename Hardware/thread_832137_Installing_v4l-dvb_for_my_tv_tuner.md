---
title: "Installing v4l-dvb for my tv tuner"
date: 2008-06-17
forum: Hardware
---

### Post by ZeldaFan on 2008-06-17
I have the tv tuner that comes with an HP dv9000t laptop. I've heard that it may work when I install the latest version of v4l-dvb. How do I go about doing that? I don't think I could simply use apt-get or synaptic.

---

### Post by mrsteveman1 on 2008-06-17
Is it a USB device? or Expresscard?

First step would be to find out whats in the device, so for usb use:

```
lsusb
```

and for expresscard i believe the bus is pci express, so:

```
lspci
```

should show it

---

### Post by ZeldaFan on 2008-06-17
It is an expresscard TV tuner. So what am I looking for in my lspci output? When I type it into the terminal, I get a lot of text, but I'm not sure what is relevant to my tv tuner's hardware.

---

### Post by mrsteveman1 on 2008-06-17
Paste all the output of lspci and i can probably tell you whats in the device and how to get a driver for it.

---

### Post by ZeldaFan on 2008-06-18
This is my lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```
By the way this is the output when the tv tuner is not inserted during bootup, I've inserted it after logging in and then typed in the lspci command.

---

### Post by mrsteveman1 on 2008-06-18
I see the PCI bridge for the PCI express ports but i don't see any devices that would be the tv tuner. hmmmmmm

I know PCI-E devices should show up, because my laptop has a few devices i know are PCI-E like the BCM94311 wireless chip, and it shows up in lspci.

What does lsusb say? there are some indications that this card might show up as a USB device for some reason on other forums.

Also some indications that some of these cards are rebranded Hauppage HVR-1600s:

> Linux support for the WinTV-HVR-1600
Linux support for the WinTV-HVR-1600 is in the upcoming kernel 2.6.26 release.

Also, there is WinTV-HVR-1600 Linux support for both the analog TV tuner and the digital TV tuner available at LinuxTV.ORG in the "cx18" section.

---

### Post by ZeldaFan on 2008-06-19
Well this is the TV tuner model I have: EC680 Analog TV tuner

And this is my lsusb output:
```
Bus 005 Device 006: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 005 Device 005: ID 03f0:3a11 Hewlett-Packard OfficeJet 5510
Bus 005 Device 004: ID 1164:0601 YUAN High-Tech Development Co., Ltd 
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

And this time I booted with the tv tuner card already in the slot, so just in case my lspci might be different here it is as well:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by ZeldaFan on 2008-06-19
Hmm...actually after looking closer at my tv tuner card, on the bottom it says it was manufactured by YUAN High-Tech Development Co., Ltd. Is this the piece of hardware found by my lsusb output?

---

### Post by lswb on 2008-06-19
Most likely the Yuan device is the TV tuner. Try opening a terminal, plugging in the card, type "dmesg" & press ENTER.

You'll see a long list of stuff scroll by and at the end will be recent changes. Look for lines that say something about "new device found" or similar phrases. If you could copy say the last screenfull or so of dmesg and paste it into a forum message here it would be helpful. BTW expresscard 34 devices are usually (maybe always? not sure) USB based, when plugged in it is like plugging in a USB card with a device attached. This allows the developers to reuse a lot of the USB driver code and makes it easier for them to make devices compatible with different systems and OSs

---

