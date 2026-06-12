---
title: "Bluetooth mouse works, not keyboard"
date: 2012-07-08
forum: Hardware
---

### Post by gladelson on 2012-07-08
I had this same problem with Ubuntu 11.04 trying to use it as a home theater PC. So, I've tried 12.04 and am getting the same results:

I have an old Microsoft Bluetooth mouse and keyboard with a USB bluetooth dongle. Ubuntu clearly recongnizes the USB adapter and turns bluetooth on. I can then add the mouse as a new device which is recognized (without pairing) and it works perfectly. When I try to add the keyboard, Ubuntu finds the device, gives me a 6-digit code for pairing which I enter and press return, and after a few seconds it says the device was added successfully. However, in the bluetooth settings the connection "button" of "off" and cannot be turned on (i.e. clicking the button does not change it to "on").

So, the system finds both devices and successfully makes a connection to the mouse, but appears to find the keyboard, clearly communicates with it to accept the PIN code but cannot turn the connection "on" after that.

I have entered the following terminal commands:

```
gary@Ubuntu-HT:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 005: ID 045e:3500 Microsoft Corp. 
Bus 002 Device 006: ID 045e:009c Microsoft Corp. Wireless Transceiver for Bluetooth 2.0
gary@Ubuntu-HT:~$ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:0D:3A:A5:DE:67  ACL MTU: 377:10  SCO MTU: 16:0
	UP RUNNING PSCAN 
	RX bytes:78225 acl:5031 sco:0 events:97 errors:0
	TX bytes:1314 acl:40 sco:0 commands:51 errors:0

gary@Ubuntu-HT:~$ hciconfig -a hci0
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:0D:3A:A5:DE:67  ACL MTU: 377:10  SCO MTU: 16:0
	UP RUNNING PSCAN 
	RX bytes:78225 acl:5031 sco:0 events:97 errors:0
	TX bytes:1314 acl:40 sco:0 commands:51 errors:0
	Features: 0xff 0xfe 0x0d 0x38 0x08 0x08 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
	Name: 'ubuntu-0'
	Class: 0x6e0100
	Service Classes: Networking, Rendering, Capturing, Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 1.2 (0x2)  Revision: 0x3
	LMP Version: 1.2 (0x2)  Subversion: 0x800
	Manufacturer: Broadcom Corporation (15)

gary@Ubuntu-HT:~$ 

```

It looks to me like the USB adapter is recognized and supported. Any ideas why I can't connect to the keyboard?

---

