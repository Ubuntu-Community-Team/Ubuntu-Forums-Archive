---
title: "bluetoth stop working"
date: 2023-11-11
forum: Hardware
---

### Post by milanh on 2023-11-11
Bluetooth working correctly, but today after resume from sleeping mode stop working. No device listed!

milan@IdeaPad-Slim-5MH:~$ uname -r; lsusb; sudo dmesg | egrep -i 'blue|firm'; hcitool dev
6.2.0-36-generic
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 30c9:00a8 Luxvisions Innotech Limited Integrated RGB Camera
Bus 001 Device 004: ID 413c:2514 Dell Computer Corp. Dell Universal Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.100767] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.301333] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.322932] [Firmware Info]: PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] not reserved in ACPI motherboard resources
[    0.342123] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    3.194383] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.195342] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.195351] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    6.820339] mt7921e 0000:03:00.0: WM Firmware Version: ____010000, Build Time: 20220209150915
[  255.739745] Bluetooth: Core ver 2.22
[  255.739783] NET: Registered PF_BLUETOOTH protocol family
[  255.739785] Bluetooth: HCI device and connection manager initialized
[  255.739790] Bluetooth: HCI socket layer initialized
[  255.739794] Bluetooth: L2CAP socket layer initialized
[  255.739798] Bluetooth: SCO socket layer initialized
[  283.992928] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  283.992934] Bluetooth: BNEP filters: protocol multicast
[  283.992939] Bluetooth: BNEP socket layer initialized
[ 7419.978695] atkbd serio0: Disabling IRQ1 wakeup source to avoid platform firmware bug
Devices:

milan@IdeaPad-Slim-5MH:~$ lspci -knn | grep Net -A3; rfkill list
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter [14c3:7961]
	DeviceName: Realtek RTL8111E Ethernet LOM
	Subsystem: Lenovo Device [17aa:e0bc]
	Kernel driver in use: mt7921e
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by milanh on 2023-11-12
this is on syslog:
Bluetooth: hci0: Opcode 0x c52 failed: -110
Bluetooth: hci0: command 0x0c52 tx timeout
Bluetooth: hci0: Opcode 0x c52 failed: -110
this means Bluetooth is dead?

---

### Post by t.c on 2024-04-10
Maybe [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051720)

---

