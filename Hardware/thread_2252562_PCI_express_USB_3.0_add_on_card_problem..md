---
title: "PCI express USB 3.0 add on card problem."
date: 2014-11-12
forum: Hardware
---

### Post by Mortars on 2014-11-12
The system I have is Ubuntu 12.04. GCC version 4.6 x86_64-linux-gnu, Xorg version 1.11.3 
I updated my Kernel from 3.2.0 to 3.8 because I read on some forum that it made a difference on USB 3.0
as to what Kernel you had. I checked the chipset on the PCI-Express card. Uses Etron EJ168A USB Host Controller IC.
Has two USB 3.0 ports and uses a SATA power connector on the back. 
When you check that card out, it is compatable with, Windows, Linux and Mac and uses the xhci driver. 
From the read outs below, it looks like it sees USB 3.0 it on BUS 009. It is turned on in the bios also. 
When I plug a USB cable and drive into it, the speed I get is 42 to 43 Mbp. Card says will run anywhere from
1.5Gbps to 5Gbps. Don't know what I'm missing here, thanks for any help you give me on this.  

lsusb:

Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

dmesg:

1.269842] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.269844] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.269860] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.269862] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.269863] usb usb9: Product: xHCI Host Controller
[    1.269864] usb usb9: Manufacturer: Linux 3.8.0-44-generic xhci_hcd
[    1.269866] usb usb9: SerialNumber: 0000:02:00.0
[    1.269944] xHCI xhci_add_endpoint called for root hub
[    1.269945] xHCI xhci_check_bandwidth called for root hub

lspci:

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

---

### Post by weatherman2 on 2014-11-12
What are you plugging into the USB 3.0 port?

Just because the port is in theory capable of transferring data at speeds of 1.5 Gbps or 3.0 Gbps doesn't mean anything you plug in to it can go that fast.

---

### Post by Mortars on 2014-11-12
A USB 3.0 drive tray with USB 3.0 cable and a WD 1TB hard drive. WD10EARS suppose to support 3.0Gb/s

---

