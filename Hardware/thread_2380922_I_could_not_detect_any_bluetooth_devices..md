---
title: "I could not detect any bluetooth devices."
date: 2017-12-23
forum: Hardware
---

### Post by alvin-nepo-o on 2017-12-23
Hi!
I just install 16.04 LTS and tried to connect my bluetooth headset and my laptop could not detect any devices. I saw this in one of the forum and tried it in the terminal.

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'

The result s are as follows:

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: Broadcom BCM43142 802.11 b/g/n 1x1Wi-Fi + BT4.0 M.2 Combo Adapter
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80b1]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 003: ID 05c8:0379 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2386:0316  
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:6D:C7:C9:3A:A2  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:1862 acl:0 sco:0 events:213 errors:0
    TX bytes:3438 acl:0 sco:0 commands:187 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'alvinnepo-HP-Pavilion-Notebook'
    Class: 0x0c010c
    Service Classes: Rendering, Capturing
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)


[    0.286148] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    2.772443] [drm] Found UVD firmware Version: 1.55 Family ID: 9
[    2.774474] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    3.259283] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x5c1f04)
[    8.652719] Bluetooth: Core ver 2.22
[    8.652747] Bluetooth: HCI device and connection manager initialized
[    8.652753] Bluetooth: HCI socket layer initialized
[    8.652756] Bluetooth: L2CAP socket layer initialized
[    8.652765] Bluetooth: SCO socket layer initialized
[    8.840128] Bluetooth: hci0: BCM: chip id 70
[    8.856810] Bluetooth: hci0: alvinnepo-HP-Pavilion-Notebook
[    8.856814] Bluetooth: hci0: BCM (001.001.011) build 0000
[    8.865163] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    8.865171] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    9.497689] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.497692] Bluetooth: BNEP filters: protocol multicast
[    9.497700] Bluetooth: BNEP socket layer initialized
[   10.899198] Bluetooth: hci0 command 0x1003 tx timeout
[   12.192086] Bluetooth: RFCOMM TTY layer initialized
[   12.192096] Bluetooth: RFCOMM socket layer initialized
[   12.192105] Bluetooth: RFCOMM ver 1.11
[  372.953841] audit: type=1107 audit(1514074553.602:37): pid=986 uid=106 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2544 label="snap.chromium.chromium" peer_pid=938 peer_label="unconfined"


I saw an error on line 8.865163 but do not know what to do next.

Please advise what to do next.

---

