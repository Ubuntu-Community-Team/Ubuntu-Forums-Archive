---
title: "libmtp commands only work in super-user mode"
date: 2009-07-19
forum: Hardware
---

### Post by Arancaytar on 2009-07-19
The problem's quite simple.

```
$ mtp-detect
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   TrekStor: i.Beat Organix 2.0 (1e68:0002) @ bus 0, dev 0
Attempting to connect device(s)
usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

```
$ sudo mtp-detect
[sudo] password for arancaytar: 
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   TrekStor: i.Beat Organix 2.0 (1e68:0002) @ bus 0, dev 19
Attempting to connect device(s)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 1e68
   idProduct: 0002
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 19
      Device entry info:
         Vendor: TrekStor
         Vendor id: 0x1e68
         Product: i.Beat Organix 2.0
         Vendor id: 0x0002
         Device flags: 0x00000002
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: 0100                                   	..
Microsoft device response to control message 1, CMD 0x01:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........

```

What do I need to do to be able to access my TrekStor player without a sudo command?

---

