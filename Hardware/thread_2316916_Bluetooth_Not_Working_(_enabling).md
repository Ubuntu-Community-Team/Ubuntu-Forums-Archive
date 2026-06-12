---
title: "Bluetooth Not Working ( enabling)"
date: 2016-03-11
forum: Hardware
---

### Post by mathan2 on 2016-03-11
bluetooth not working well , i use 14.04 LTS

---

### Post by jeremy31 on 2016-03-12
Copy the following command and use your mouse/touchpad or CTRL + Shift + v to paste into terminal, press enter
```
uname -r; rfkill list all; lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'
```

Post the results

---

### Post by mathan2 on 2016-03-13
```
3.13.0-83-generic
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
01:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
    Kernel driver in use: rt61pci
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:8119] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8119]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8300] [10de:0848] (rev a2)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:0061 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    1.212321] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[   16.162906] Bluetooth: Core ver 2.17
[   16.162941] Bluetooth: HCI device and connection manager initialized
[   16.162955] Bluetooth: HCI socket layer initialized
[   16.162958] Bluetooth: L2CAP socket layer initialized
[   16.162962] Bluetooth: SCO socket layer initialized
[   23.106120] Bluetooth: RFCOMM TTY layer initialized
[   23.106137] Bluetooth: RFCOMM socket layer initialized
[   23.106143] Bluetooth: RFCOMM ver 1.11
[   23.264816] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.264821] Bluetooth: BNEP filters: protocol multicast
[   23.264834] Bluetooth: BNEP socket layer initialized
[   28.787900] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   28.939003] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
```

but its work  well on windows 10 pro

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by jeremy31 on 2016-03-13
I would install the 4.2 kernel from Wily and see if it works
```
sudo apt-get install linux-generic-lts-wily
```

reboot

---

