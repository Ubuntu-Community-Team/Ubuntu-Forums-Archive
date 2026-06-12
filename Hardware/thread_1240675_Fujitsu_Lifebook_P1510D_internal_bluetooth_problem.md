---
title: "Fujitsu Lifebook P1510D internal bluetooth problem"
date: 2009-08-15
forum: Hardware
---

### Post by routinepursuit on 2009-08-15
Cannot get bluetooth working on Fujitsu Lifebook P1510D with Jaunty 9.04.
Unit appears to have internal bluetooth and I know about the kill switch for the wifi and rf on the side of the unit.  I read something the eluded to that it must be turned on under Windows for it to work from then on.  There has got to be a way to get this to play ball without going back to a Windows intsall.  I dont have the recovery disk, send me one?  Anyway here are some system details...

dmesg output

[    1.413410] Bluetooth: Core ver 2.13
[    1.413410] Bluetooth: HCI device and connection manager initialized
[    1.413410] Bluetooth: HCI socket layer initialized
[    4.125850] Bluetooth: L2CAP ver 2.11
[    4.125856] Bluetooth: L2CAP socket layer initialized
[    4.125863] Bluetooth: SCO (Voice Link) ver 0.6
[    4.125869] Bluetooth: SCO socket layer initialized
[    4.125932] Bluetooth: RFCOMM socket layer initialized
[    4.125948] Bluetooth: RFCOMM TTY layer initialized
[    4.125954] Bluetooth: RFCOMM ver 1.10
[   25.743106] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.743111] Bluetooth: BNEP filters: protocol multica

hciscan output

hcitool scan
No such device

lspci output

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
06:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
06:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:05.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01

lsusb output

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 ro

---

