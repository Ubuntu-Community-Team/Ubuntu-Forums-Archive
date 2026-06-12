---
title: "Bluetooth doesn't find any device"
date: 2018-05-03
forum: Hardware
---

### Post by kalenz2 on 2018-05-03
Hello,

I have been trying to connect several bluetooth headsets to my laptop, I have dual boot, on windows it works but on ubuntu i cannot find any active device, even when i know that they are here. I have tried using terminal to scan with** bluetoothctl** and** scan on**. It looks like it is on but i wont find anything. I have seen somewhere similar problem where they asked the user to post result of** lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm' **so I guess it might help if I post it here.

```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: AzureWave QCA9565 / AR9565 Wireless Network Adapter [1a3b:218d]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3490 IMC Networks 
Bus 001 Device 003: ID 04f2:b52b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 80:A5:89:41:3F:C6  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN ISCAN 
    RX bytes:916 acl:0 sco:0 events:89 errors:0
    TX bytes:3752 acl:0 sco:0 commands:86 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'daniel-X556UB'
    Class: 0x0c010c
    Service Classes: Rendering, Capturing
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x3101
    LMP Version: 4.0 (0x6)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)

[    0.200156] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   21.361220] Bluetooth: Core ver 2.21
[   21.361234] Bluetooth: HCI device and connection manager initialized
[   21.361238] Bluetooth: HCI socket layer initialized
[   21.361240] Bluetooth: L2CAP socket layer initialized
[   21.361245] Bluetooth: SCO socket layer initialized
[   40.648904] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.648906] Bluetooth: BNEP filters: protocol multicast
[   40.648909] Bluetooth: BNEP socket layer initialized
[   62.193898] Bluetooth: RFCOMM TTY layer initialized
[   62.193904] Bluetooth: RFCOMM socket layer initialized
[   62.193907] Bluetooth: RFCOMM ver 1.11


```
 .

Thank you for your time

---

