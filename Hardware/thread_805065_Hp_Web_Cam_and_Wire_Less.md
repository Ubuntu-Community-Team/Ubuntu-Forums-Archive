---
title: "Hp Web Cam and Wire Less"
date: 2008-05-23
forum: Hardware
---

### Post by u.law on 2008-05-23
Is it possible to activate my Web Cam and Wireless ?
I have a Hp 9704tx Laptop.

Thanks Everyone

---

### Post by bwhite82 on 2008-05-23
First, provide more information to those who may be able to help you. Post here, the results of two commands:

> lspci

and

> lsusb

---

### Post by u.law on 2008-05-23
Result of lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by u.law on 2008-05-23
Result of lsusb:

Bus 007 Device 003: ID 04f2:b023 Chicony Electronics Co., Ltd 

Bus 007 Device 001: ID 0000:0000  

Bus 005 Device 001: ID 0000:0000  

Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 002: ID 046d:c019 Logitech, Inc. 

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 001: ID 0000:0000  

Bus 006 Device 001: ID 0000:0000

---

### Post by hotweiss on 2008-05-24
The web cam is no problem, just follow these instructions:

A) First we&#8217;ll need to install the files needed to build the driver by typing the following in Terminal:
> sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
> cd /usr/src
and then
> sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
> cd trunk
and then
> sudo make
and then
> sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.


Here are some instructions on how to get your wifi working:

[http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

---

