---
title: "USB Flash drive not mounting"
date: 2010-12-16
forum: Hardware
---

### Post by Temporary Saint on 2010-12-16
I have a Kingston 2GB flash drive that used to mount fine in Linux Mint Isadora 32-bit. Now it (or any other USB storage device) will not mount if it's not connected to the laptop at boot. Gparted does not show it as an available device, nor does fstab. lsusb displays it however:

Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel
Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 059b:0278 Iomega Corp.
Bus 001 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100 - THIS IS THE DEVICE IN QUESTION
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg displays:
[17002.164059] usb 1-7: new high speed USB device using ehci_hcd and address 4
[17002.298992] usb 1-7: configuration #1 chosen from 1 choice

Can I mount it manually without it having a device name (sda1, etc.)?

Steve

---

### Post by Temporary Saint on 2010-12-21
Aw jeez, you're kidding, folks.  I stumped you all?  No ideas? :(

---

### Post by Tamrac on 2010-12-21
Same problem here dude..... all my USB sticks do not mount. But they all show up on Ubuntu's Disk Utility app. Weird....:confused:

---

