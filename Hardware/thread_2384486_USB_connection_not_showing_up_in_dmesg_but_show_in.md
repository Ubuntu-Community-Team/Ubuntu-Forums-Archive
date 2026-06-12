---
title: "USB connection not showing up in dmesg but show in lsusb"
date: 2018-02-07
forum: Hardware
---

### Post by alecz20 on 2018-02-07
I have a laptop and I encountered a strange issue after resuming from suspend:
No USB devices work (except a USB fan).

When I connect the keyboard, there is no reaction, the "Lock" LEDs that normally blink stay silent, and there is nothing logged in dmesg or syslog, however, lsusb shows the devices:

$ lsusb
Bus 002 Device 004: ID 04f2:b315 Chicony Electronics Co., Ltd
Bus 002 Device 003: ID 0483:91d1 STMicroelectronics Sensor Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:21f3 Broadcom Corp.
Bus 001 Device 003: ID 03eb:8206 Atmel Corp.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 2109:0813 VIA Labs, Inc.
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c06d Logitech, Inc.
Bus 003 Device 003: ID 2109:2813 VIA Labs, Inc.
Bus 003 Device 002: ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Since this is a laptop, its keyboard and touchpad work, but no external USB devices function.

Rebooting solved the USB keyboard detection issue, but after logging in, there's just the desktop background, no bars, no icons, no cursor... Well, that's another issue.

Does anyone have any idea why dmesg stays silent when connecting/disconnecting USB devices and lsusb shows them even if they are disconnected?

---

