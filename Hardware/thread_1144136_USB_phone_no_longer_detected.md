---
title: "USB phone no longer detected"
date: 2009-04-30
forum: Hardware
---

### Post by erickatz on 2009-04-30
I have an LG Decoy that I plug in via USB.  Prior to Jaunty (with Intrepid), as soon as I plugged the phone in Ubuntu would automatically detect the phone's existence, and present me with the opportunity to configure the phone.  Additionally, BitPim also worked swimmingly.  Now, after the Jaunty upgrade, neither of these is true.  The ability to configure is gone, and BitPim won't recognize the phone.

Here's the lsusb result, the phone is listed at Bus 003, Device 004:
Bus 001 Device 009: ID 413c:2010 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:1003 Dell Computer Corp. 
Bus 001 Device 006: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 010: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 008: ID 0424:2602 Standard Microsystems Corp. 
Bus 001 Device 005: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 004: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 003 Device 003: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Here's the /var/log/messages:

Apr 30 13:32:57 rswekatz kernel: [19256.864057] usb 3-2: new full speed USB device using uhci_hcd and address 4
Apr 30 13:32:58 rswekatz kernel: [19257.026599] usb 3-2: configuration #1 chosen from 1 choice
Apr 30 13:32:58 rswekatz kernel: [19257.295311] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
Apr 30 13:32:58 rswekatz kernel: [19257.298243] usbcore: registered new interface driver cdc_acm
Apr 30 13:32:58 rswekatz kernel: [19257.298251] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

---

### Post by billmania on 2011-02-05
Did you ever solve this problem? I'm trying to transfer photos from a Samsung SCH-U640 to a 32 bit 10.04.2 LTS notebook, so far without success.

---

