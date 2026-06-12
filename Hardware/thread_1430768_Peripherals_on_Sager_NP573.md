---
title: "Peripherals on Sager NP573"
date: 2010-03-15
forum: Hardware
---

### Post by GL92 on 2010-03-15
Hi all,

I am running Linux Mint 8 X64 (helena) and am having trouble getting recognition of my peripherals.

These include a fingerprint scanner, microphone and  webcam (all built into the design).

I have read that the fingerprint scanners are very finicky with Linux and are tough to get working, so I would like to concentrate on the camera and microphone first!

I want to use the camera with skype but it does not register with the program.

Thanks in advance guys!

---

### Post by GL92 on 2010-03-16
ttt

---

### Post by Muzer on 2010-03-16
Give the output of the following commands:

lspci -nn

lsusb


(the first lists all PCI devices with their device numbers and names, which is a common way to plug devices in internally; the other lists all USB devices with device numbers and names, which is less common but still possible).

---

### Post by GL92 on 2010-03-16
> **Muzer said:**
> Give the output of the following commands:

lspci -nn

lsusb


(the first lists all PCI devices with their device numbers and names, which is a common way to plug devices in internally; the other lists all USB devices with device numbers and names, which is less common but still possible).

 Heres the lspci -nn  > 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03) 00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03) 00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) 00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) 00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) 00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03) 00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) 00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8700M GT] [10de:0409] (rev a1) 06:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236] 08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01) 0c:07.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730] 0c:07.1 SD Host controller [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller [1524:0750] 0c:07.3 FLASH memory [0501]: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller [1524:0751] 0c:09.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev c0)  And the lsusb:  >  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

---

### Post by GL92 on 2010-03-18
ttt  anyone?

---

