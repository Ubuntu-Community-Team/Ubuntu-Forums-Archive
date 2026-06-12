---
title: "Mobile Philips X800 as webcam"
date: 2009-05-19
forum: Hardware
---

### Post by Pretorean on 2009-05-19
I use ubuntu 9.04

uname -a
```
Linux d6550 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux

```

after connect phone

dmesg
```
[149536.136015] usb 8-1: new full speed USB device using uhci_hcd and address 2
[149536.600352] usb 8-1: configuration #1 chosen from 7 choices
[149536.788588] Linux video capture interface: v2.00
[149536.815190] uvcvideo: Found UVC 1.00 device X800    (0e8d:0004)
[149537.817041] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[149537.819036] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -71 (exp. 26).
[149537.819038] uvcvideo: Failed to initialize the device (-5).
[149537.819083] usbcore: registered new interface driver uvcvideo
[149537.819086] USB Video Class driver (v0.1.0)
[149985.360047] usb 8-1: USB disconnect, address 2
[149997.340514] usb 8-1: new full speed USB device using uhci_hcd and address 3
[149997.804314] usb 8-1: configuration #1 chosen from 7 choices
[149997.823102] uvcvideo: Found UVC 1.00 device X800    (0e8d:0004)
[149998.822035] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[149998.824042] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -71 (exp. 26).
[149998.824047] uvcvideo: Failed to initialize the device (-5).
[150150.032046] usb 8-1: USB disconnect, address 3
[150158.748025] usb 8-1: new full speed USB device using uhci_hcd and address 4
[150159.268420] usb 8-1: configuration #1 chosen from 7 choices
[150159.278046] uvcvideo: Found UVC 1.00 device X800    (0e8d:0004)
[150160.278059] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[150160.280275] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -71 (exp. 26).
[150160.280278] uvcvideo: Failed to initialize the device (-5).

```

lsusb
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0e8d:0004 MediaTek Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04e8:300c Samsung Electronics Co., Ltd ML-1210 Printer
Bus 003 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

What can I do?
thanks

---

