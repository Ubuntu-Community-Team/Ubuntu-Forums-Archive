---
title: "USB Bluetooth Dongle issues with accepting address:"
date: 2010-01-07
forum: Hardware
---

### Post by rosier on 2010-01-07
Hi I need some help installing a USB bluetooth dongle, Ive tried two dongles and neither adapters is installed by Hardy.

Ive tried all USB ports and have confirmed that the dongles work on fedora.
Checking the logs when i connect the adapter i get the following output.

Heres some data
dad@dad-desktop:~$ lsusb
   Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
   Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
   Bus 003 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
   Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
   Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
   Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dad@dad-desktop:~$ 

here is a report from dmesg report when unplugging and replugging:

   [ 2494.860061] usb 4-1: new full speed USB device using uhci_hcd and address 15
   [ 2494.980029] usb 4-1: device descriptor read/64, error -71
   [ 2495.204035] usb 4-1: device descriptor read/64, error -71
   [ 2495.420036] usb 4-1: new full speed USB device using uhci_hcd and address 16
   [ 2495.836091] usb 4-1: device not accepting address 16, error -71
   [ 2495.948030] usb 4-1: new full speed USB device using uhci_hcd and address 17
   [ 2496.356021] usb 4-1: device not accepting address 17, error -71
   [ 2496.356046] hub 4-0:1.0: unable to enumerate USB device on port 1

  picks up my webcam or USB pendrives can anyone advise hoe to resolve the "device not accepting address17, error 71"
Ive tried both dongles on Karmic and exactly the same faulTt!!!

HHHHEEEELLLLPP!!

---

