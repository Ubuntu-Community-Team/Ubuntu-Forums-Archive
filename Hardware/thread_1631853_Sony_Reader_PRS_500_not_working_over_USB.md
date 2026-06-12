---
title: "Sony Reader PRS 500 not working over USB"
date: 2010-11-27
forum: Hardware
---

### Post by rajeshja on 2010-11-27
I have a first generation Sony Reader (PRS-500), and have used it with Ubuntu in the past. I sometimes had trouble transferring books to it over Calibre, but much of the time I could connect to it.

Sometime in the past, this stopped working. When I connect the device to my PC using a USB cable, I see messages like the following:

```
[20520.320016] usb 3-2: new full speed USB device using uhci_hcd and address 6

```
When I disconnect the USB cable, dmesg gives me the following message:

```
[20744.040558] usb 3-2: USB disconnect, address 6

```

Running lsusb gives me the following output:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 004 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 054c:029b Sony Corp. PRS-500 eBook reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But calibre doesn't detect the device, and it doesn't show up mounted as an external/removal drive either.

What I'd like to know is, how do I go about debugging this situation? What is missing? The same device works without issues on a 5 year old Dell Windows XP laptop.

Any suggestions?

---

