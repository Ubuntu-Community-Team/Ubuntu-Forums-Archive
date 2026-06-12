---
title: "USB connectivity: wifi adapter and BT keyboard disconnects, BT mouse unaffected."
date: 2024-10-22
forum: Hardware
---

### Post by oau on 2024-10-22
Hey all,
I'm having issues with my USB devices after upgrading to 24.04.
My USB wifi adapter (D-LINK ax 1800) and BT keyboard with a USB dongle (logitec) keeps disconnecting. It can happen a short while after I use the devices, not enough time for entering some sort of hibernation. They can (but not necessarily) disconnect simultaneously. It happens A LOT - every few minutes.
The BT mouse that interacts with the same USB dongle as the keyboard works fine.
I read that it might be related to the autosuspend parameter of usbcore so I've modified it to -1.
I think i might had some minor issues recently while using 22.04, but not at the same frequency as now, this is intolerable.
Any help would be appreciated

lsusb output:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 048d:5702 Integrated Technology Express, Inc. RGB LED Controller
Bus 001 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0424:2734 Microchip Technology, Inc. (formerly SMSC) USB2734
Bus 003 Device 004: ID 0424:274c Microchip Technology, Inc. (formerly SMSC) Hub Controller
Bus 003 Device 005: ID 2001:3321 D-Link Corp. 802.11ac WLAN Adapter
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 0424:5734 Microchip Technology, Inc. (formerly SMSC) USB5734

```

Thanks!

---

