---
title: "Ubuntu can't see ext4 drive after mounting in windoze"
date: 2016-04-26
forum: Hardware
---

### Post by martinkellner on 2016-04-26
Edit: Appears it was the result of a broken USB cable /:


I mounted my external ext4 drive in windows using diskinternals linux reader to copy a few files to another computer. It's a seagate 500 gb USB drive and I (still) run ubuntu 14.04. When I reconnected it to my ubuntu computer ubuntu doesn't even see the drive. Nothing comes up if I runt gparted and lsusb outputs:

Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 1bcf:2802 Sunplus Innovation Technology Inc. 
Bus 001 Device 008: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 007: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Since ubuntu doesn't even see the drive, I don't even know where to start troubleshooting. What's wrong here?

---

