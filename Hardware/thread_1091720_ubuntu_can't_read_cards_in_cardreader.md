---
title: "ubuntu can't read cards in cardreader"
date: 2009-03-09
forum: Hardware
---

### Post by ewientje on 2009-03-09
Hi, I'm new at Ubuntu, just installed Ubuntu on my pc.
Everything seems to work fine, except that ubuntu does'nt recognize that i plug in a sd card in the cardreader.

So how do I get Ubuntu to recognize the cardreaders.

---

### Post by stchman on 2009-03-09
> **ewientje said:**
> Hi, I'm new at Ubuntu, just installed Ubuntu on my pc.
Everything seems to work fine, except that ubuntu does'nt recognize that i plug in a sd card in the cardreader.

So how do I get Ubuntu to recognize the cardreaders.

We will need some more information.

1.  Laptop model number.
2.  Post and lspci output here in this thread.

---

### Post by ewientje on 2009-03-10
it is not a laptop, it is a medion aldi pc.
intel pentium 3ghz 3ghz, 2 gb ram. With Vista Home Premium dualbooting with Ubuntu 8.10.
He found the sata drives, the idee drives, the philips(music ipod kind of thingy), the maxtora etc, but not the cardreaders.

There are 3 cardreaders, c-media usb cardreader.

What is lspci output ?

---

### Post by stchman on 2009-03-10
> **ewientje said:**
> it is not a laptop, it is a medion aldi pc.
intel pentium 3ghz 3ghz, 2 gb ram. With Vista Home Premium dualbooting with Ubuntu 8.10.
He found the sata drives, the idee drives, the philips(music ipod kind of thingy), the maxtora etc, but not the cardreaders.

There are 3 cardreaders, c-media usb cardreader.

What is lspci output ?

The lspci command lists all the hardware connected to the PCI bus.  The lsusb command lists all the hardware connected via USB.

Open a terminal.

Type lspci.

Post the output in this thread.

Type lsusb.

Post the output in this thread.  Also a complete model number of the might be helpful as well.

---

### Post by ewientje on 2009-03-10
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6700 XL (rev a2)
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Communication controller: Agere Systems Device 0620

corrie@ubuntu:~$ lsusb
Bus 005 Device 006: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 005 Device 005: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Bus 005 Device 003: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0471:084a Philips 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
corrie@ubuntu:~$ 

Medion Md 8000 series

---

### Post by ewientje on 2009-03-11
I was trying to install an epson photoscanner, wasn't succesfull, but I got this.

found USB scanner (vendor=0x0bc7, product=0x0006) at libusb:005:007
found USB scanner (vendor=0x148f, product=0x2570) at libusb:005:006
found USB scanner (vendor=0x0d8c, product=0x5200) at libusb:005:003

corrie@ubuntu:~$ scanimage -L
device `v4l:/dev/video1' is a Noname Medion Md8800 Quadro virtual device
device `v4l:/dev/video0' is a Noname Medion Md8800 Quadro virtual device

I don;t think they are scanners, but they are my flash drives.
So what do I do know.
Please help ??

---

