---
title: "Bluetooth neither is visible nor finds devices"
date: 2016-03-09
forum: Hardware
---

### Post by Donato_Lorenzo on 2016-03-09
Hi,

 my laptop's Bluetooth adapter seems to be ok: blueman detects it, panel icon is ok, service is started on so startup...

But it's not visible for other devices, neither it finds others. So, does nothing xD

 My laptop is a [Toshiba L50D-C-13P]("http://www.toshiba.es/laptops/satellite/satellite-l50-c/satellite-l50d-c-13p/") with XUbuntu 15.10.

 Here is some info:

```

$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux makinita 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:f840]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b730]
    Kernel driver in use: rtl8723be
Bus 003 Device 003: ID 1a81:1006 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0930:0222 Toshiba Corp. 
Bus 001 Device 002: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    3.088447] usb 1-2: Product: Bluetooth Radio 
[   11.061494] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[   12.245129] Bluetooth: Core ver 2.20
[   12.245171] Bluetooth: HCI device and connection manager initialized
[   12.245181] Bluetooth: HCI socket layer initialized
[   12.245186] Bluetooth: L2CAP socket layer initialized
[   12.245195] Bluetooth: SCO socket layer initialized
[   25.463010] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.463016] Bluetooth: BNEP filters: protocol multicast
[   25.463026] Bluetooth: BNEP socket layer initialized
[   45.803224] Bluetooth: RFCOMM TTY layer initialized
[   45.803241] Bluetooth: RFCOMM socket layer initialized
[   45.803253] Bluetooth: RFCOMM ver 1.11
[    1.123816] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.197646] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    2.469641] [drm] Found UVD firmware Version: 1.45 Family ID: 11
[    2.470595] [drm] Found VCE firmware Version: 50.17 Binary ID: 3
[    2.966536] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x5e1f02)
[   12.886448] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
bluetooth             516096  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
toshiba_bluetooth      16384  0

```

```
$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: B8:86:87:A1:8B:5F  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING PSCAN ISCAN 
    RX bytes:772 acl:0 sco:0 events:63 errors:0
    TX bytes:4293 acl:0 sco:0 commands:63 errors:0

```

Maybe two entries here as wireless devices is a signal:
```
$ rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


I added this lsmod info, just in case this "btcoexist" has something to do:
```
$ lsmod | grep -i "bt" ; lsmod | grep -i "rtl"
btcoexist              53248  1 rtl8723be
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
rtl8723be              86016  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              733184  3 rtl_pci,rtlwifi,rtl8723be
btrtl                  16384  1 btusb
bluetooth             516096  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              548864  2 mac80211,rtlwifi

```


Probably I have to install some drivers, as I did for WiFi card, and what I never did for Bluetooth. In that case... how would I detect the drivers I need? :/

Or the problem may be anything else...I really googled it, but my Linux skills aren't still enough to link all the info about devices,modules,drivers... *_*  

Thanks a lot!

Regards,

---

### Post by jeremy31 on 2016-03-10
[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

Please file a bug report as this one isn't supported in upstream kernels, also include ```
usb-devices | awk '/0222/' RS=
```

---

