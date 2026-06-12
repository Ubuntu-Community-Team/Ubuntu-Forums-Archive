---
title: "SD Card reader not working"
date: 2012-01-02
forum: Hardware
---

### Post by nawab_sahab on 2012-01-02
Laptop: HP dv6000
OS: Ubuntu 11.10
SD.MS/Pro.MMC.XD reader attached to the laptop
Cards tried - 1. PNY Micro SD on SD adapter (2GB) 2. Dane-Elec SD card (256MB) 


Both cards work fine in windows but nothing happens in Ubuntu.

Tried lspci below is the output

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev ff)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev ff)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Can someone help this newbie??

---

### Post by nawab_sahab on 2012-01-03
Did a little research and here is what I get from lspci

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev ff)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev ff)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Any one know what to do from here?

---

### Post by bluexrider on 2012-01-03
So, i do not understand! Are you trying to access using bluetooth or USB card reader?

---

### Post by efflandt on 2012-01-04
See what the tail end of **dmesg** shows after inserting an SD card.  A built-in card reader is often USB connected on desktops, but often NOT a USB device on laptops, so you may need to see what other block device it is and manually mount a partition on it.  That was the case with my older Toshiba laptop from 2006.  Because it was not USB, it could not boot from it and its internal card reader was NOT able to handle higher speed SD cards or SDHC.  Although, external USB worked fine, including booting any SD/microSD reader, memory stick, or hard drive.

Fortunately the internal SD slot in my new tablet PC (Acer Iconia W500P) is connected internally via USB, so I was able to install and can boot Ubuntu from 16 GB SDHC, without tampering with its Win7 Pro SSD.

---

### Post by nawab_sahab on 2012-01-10
It is an internal sd card reader attached with the computer. It is not USB connected or Bluetooth connected. here is what lspci gives

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev ff)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev ff)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Mark Phelps on 2012-01-11
I have a similar problem with my PC in that is does not "see" the internal card reader in Linux.  It works FINE in Win7!

My "solution" was to buy a cheap USB-connected external card reader.  Since it connects via USB, it also works fine.

Solution is a bit clumsy, but it works.

---

### Post by flemur13013 on 2012-01-11
FWIW, my built-in SD card reader disappears until reboot, or maybe  logout/in, if I do a "Safely remove drive" in nautilus; "Eject" works fine.

---

### Post by MrKimi on 2012-01-11
My SD card reader has stopped working since upgrading to 11.10.
It took me a while to notice because I rarely use the SD reader.
I have two cards and they both work on a Windows machine.
Both machines are Dell Inspiron 9400 laptops.

I tried inserting the card and rebooting but nothing.
To be clear, what I used to see was a reference to the card in Natilus similar to when I insert a USB drive.
I don't see that reference now. USB drives work fine, though.

roger@Ambrose:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

Any ideas?
Thanks

---

### Post by nawab_sahab on 2012-01-15
> **MrKimi said:**
> My SD card reader has stopped working since upgrading to 11.10.
It took me a while to notice because I rarely use the SD reader.
I have two cards and they both work on a Windows machine.
Both machines are Dell Inspiron 9400 laptops.

I tried inserting the card and rebooting but nothing.
To be clear, what I used to see was a reference to the card in Natilus similar to when I insert a USB drive.
I don't see that reference now. USB drives work fine, though.

roger@Ambrose:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

Any ideas?
Thanks


MrKim try 

lspci 

and see if it is pci connected. Mine is pci connected and thus screwed.

---

### Post by MrKimi on 2012-01-15
> **nawab_sahab said:**
> MrKim try 

lspci 

and see if it is pci connected. Mine is pci connected and thus screwed.

Sure. Here's my output:
roger@Ambrose:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

This output does not change if the SD card is present or not. This seems to be showing all devices (including hard drive, wifi and USB) and it is also showing "Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)" can I conclude that the SD card reader is connected via PCI? Why does that mean it is a problem? It wasn't under my previous version of Ubuntu (10.10)

Thanks for the help.
R

---

### Post by nawab_sahab on 2012-01-15
Yes you are on pci. Here is a solution, it did not work for me I hope it works for you.

[http://ubuntuforums.org/showthread.php?t=636867](http://ubuntuforums.org/showthread.php?t=636867)

---

### Post by dariusz21p on 2012-04-12
I have the same problem with my HP Pavilion dv6500 Notebook PC after upgrading from 11.04 to 11.10

Before card reader worked fine, but not any more even with the latest kernel. 

output from lcpci:

07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at b0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

I can see bug open for this, but there is no workaround I can see
[https://bugs.launchpad.net/ubuntu/+bug/311781](https://bugs.launchpad.net/ubuntu/+bug/311781) 

cheers

Dariusz

---

