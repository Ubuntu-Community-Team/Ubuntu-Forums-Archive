---
title: "Strange trackpad activity"
date: 2015-03-28
forum: Hardware
---

### Post by Ertai87 on 2015-03-28
Hi all!  I've been having an ongoing problem with my trackpad on Ubuntu.  My computer is a Toshiba Satellite C40D-A.  The issue seems to be that when the computer is not held perfectly flat, the trackpad responds strangely; it loses sensitivity in places, gains sensitivity in others, etc, causing the cursor to fling about the screen.  Furthermore, I think there's a line in my trackpad where it cancels the input if I run over it, which is a pain.  None of these problems exist if I use Windows, and if I use a USB mouse it works fine, so I'm pretty sure it's not a hardware thing.  Any ideas?  Thanks.

---

### Post by Vladlenin5000 on 2015-03-29
You're right about it being most likely software/drivers related... 
Can you post the exact device you have? *lsusb* or *lspci* (one of them) should give the information.

---

### Post by Ertai87 on 2015-03-29
```
$ lsusb
Bus 002 Device 002: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)

```

---

