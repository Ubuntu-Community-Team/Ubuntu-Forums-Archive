---
title: "Ubuntu 16.04 - Can't detect BT devices"
date: 2016-10-19
forum: Hardware
---

### Post by boanerxe on 2016-10-19
Dear all,
I have a problem with Ubuntu 16.04. I can't detect any BT devices. 
I have a PCIe wifi card including BT 4.0. It is detected by Ubuntu, but when I try to scan for devices, it doen't discover any device.

I have searched the forum for similar threads, but I could't find a suitable solution for my card.

Here is the output for the following command, as it can help to identify my hardware:
```

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: ASUSTeK Computer Inc. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1043:207f]
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b54b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 30:5A:3A:8C:D1:DB  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING 
    RX bytes:1085 acl:0 sco:0 events:102 errors:0
    TX bytes:18082 acl:0 sco:0 commands:103 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)
[    0.215950] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    3.071115] usb 1-4: Product: Bluetooth Radio 
[   13.763217] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   13.763232] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   14.570896] Bluetooth: Core ver 2.21
[   14.570936] Bluetooth: HCI device and connection manager initialized
[   14.571092] Bluetooth: HCI socket layer initialized
[   14.571099] Bluetooth: L2CAP socket layer initialized
[   14.571118] Bluetooth: SCO socket layer initialized
[   15.307695] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   15.307705] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   15.408644] Bluetooth: hci0: rom_version status=0 version=1
[   24.752233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.752240] Bluetooth: BNEP filters: protocol multicast
[   24.752249] Bluetooth: BNEP socket layer initialized
[   26.886936] Bluetooth: hci0 command 0x0c56 tx timeout
[  167.308824] Bluetooth: RFCOMM TTY layer initialized
[  167.308840] Bluetooth: RFCOMM socket layer initialized
[  167.308857] Bluetooth: RFCOMM ver 1.11
```

Any help will be appreciated!

---

### Post by mörgæs on 2016-10-20
> **boanerxe said:**
> 
[    0.215950] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored


This looks interesting. Do you get same output with 16.10?

---

### Post by jeremy31 on 2016-10-20
I would try discovering other devices in terminal
```
bluetoothctl
power on
scan on
```
And wait to see if you get an error. Use CTRL + d to quit bluetoothctl

---

