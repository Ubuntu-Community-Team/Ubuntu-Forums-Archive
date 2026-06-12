---
title: "Creative Zen V and Amarok"
date: 2009-01-15
forum: Hardware
---

### Post by the hoplite on 2009-01-15
Hi everybody,

I'm new to Ubuntu and really enthusiastic about it so I'm switching completly from Win. So I'm trying to connect my Creative Zen V plus to Amarok for file transfering and even if the device should be supported, clicking the Connect device thing it doesn't work. I've tried various solutions, but my Ubuntu knowledge is very limited. 
So if I type:

lu@lu-laptop:~$ lsusb
Bus 007 Device 006: ID 041e:4152 Creative Technology, Ltd 
Bus 007 Device 004: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 007 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 064e:a101 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

then..
lu@lu-laptop:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN V Plus (041e:4152) @ bus 0, dev 6
Attempting to connect device(s)
PTP: Opening session
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4152
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 6
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN V Plus
         Vendor id: 0x4152
         Device flags: 0x00000000   (..........)

Sorry for the long post. So the device itself is seen by the system but Amarok cannot detect it. Can anybody help me? Thanks...

---

### Post by the hoplite on 2009-01-16
It was just a problem of Amarok settings, choosing MTP media device in devices setting window the problem disappears. Amarok is impressive!!

---

