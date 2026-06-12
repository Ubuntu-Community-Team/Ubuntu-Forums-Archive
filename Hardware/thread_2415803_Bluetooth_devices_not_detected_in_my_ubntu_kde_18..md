---
title: "Bluetooth devices not detected in my ubntu kde 18.04 (dell inspiron 15)"
date: 2019-04-01
forum: Hardware
---

### Post by harshas on 2019-04-01
Bluetooth not working properly. I haven't found any bluetooth devices in bluetooth device scanning, though i have bluetooth devices like phone,speaker,headset in ubuntu kde 18.04. i ran this command in terminal and get this.
command:[FONT=monospace][COLOR=#000000]uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep [/COLOR]-i firmware; lsmod | grep bluetooth
[/FONT][FONT=monospace][COLOR=#000000]Linux shk-Inspiron-3543 4.15.0-46-generic #49-Ubuntu SMP Wed Feb 6 09:33:07 UTC 2019 x86_64 x86_64 x86_64 GNU/[/COLOR]
Linux
06:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)[/COLOR]
        Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
        Kernel driver in use: wl
[COLOR=#18B2B2]--[/COLOR]
07:00.0 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] control[/COLOR]
ler [10ec:8136] (rev 07)
        Subsystem: Dell RTL810xE PCI Express Fast Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [1028:0654][/COLOR]
        Kernel driver in use: r8169
        Kernel modules: r8169
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0bda:5756 Realtek Semiconductor Corp.  
Bus 001 Device 003: ID 1ea7:0066   
Bus 001 Device 002: ID 8087:8001 Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0461:4d81 Primax Electronics, Ltd Dell N889 Optical Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   23.661385] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: Core ver 2.22[/COLOR]
[   23.661411] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: HCI device and connection manager initialized[/COLOR]
[   23.661414] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: HCI socket layer initialized[/COLOR]
[   23.661416] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: L2CAP socket layer initialized[/COLOR]
[   23.661422] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: SCO socket layer initialized[/COLOR]
[   23.782205] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: chip id 70[/COLOR]
[   23.783192] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: features 0x06[/COLOR]
[   23.799207] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM43142A[/COLOR]
[   23.799223] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM (001.001.011) build 0000[/COLOR]
[   23.829459] [COLOR=#FF5454]**bluetooth**[/COLOR][COLOR=#000000] hci0: Direct firmware load for brcm/BCM.hcd failed with error -2[/COLOR]
[   23.829462] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: Patch brcm/BCM.hcd not found[/COLOR]
[   25.856048] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: command 0x1003 tx timeout[/COLOR]
[   29.314830] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[   29.314832] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP filters: protocol multicast[/COLOR]
[   29.314836] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP socket layer initialized[/COLOR]
[   31.328066] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: command 0x1003 tx timeout[/COLOR]
[   96.747230] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM TTY layer initialized[/COLOR]
[   96.747250] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM socket layer initialized[/COLOR]
[   96.747266] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM ver 1.11[/COLOR]
[ 9243.468196] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9259.341129] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9275.470244] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9291.343271] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9307.473148] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9323.345162] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9339.475172] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9355.347187] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9371.477177] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9387.349182] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9403.478220] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9419.356210] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9435.481207] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[ 9451.354229] [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: last event is not cmd complete (0x0f)[/COLOR]
[    0.028331] Spectre V2 : Enabling Restricted Speculation for [COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000] calls[/COLOR]
[    0.060457] ACPI: [[COLOR=#FF5454]**Firmware**[/COLOR][COLOR=#000000] Bug]: BIOS _OSI(Linux) query ignored[/COLOR]
[   23.829459] bluetooth hci0: Direct [COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000] load for brcm/BCM.hcd failed with error -2[/COLOR]
[COLOR=#FF5454]**bluetooth**[/COLOR][COLOR=#000000]             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm[/COLOR]
ecdh_generic           24576  2 [COLOR=#FF5454]**bluetooth**[/COLOR]

[/FONT]
Please help me to pair bluetooth devices in ubuntu kde 18.04 in my laptop dell inpsiron 3543 .

---

### Post by VMC on 2019-04-01
Have you checked the firmware to see if yours is listed.

---

