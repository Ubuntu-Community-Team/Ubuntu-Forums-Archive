---
title: "How to set up USB serial port?"
date: 2010-07-15
forum: Hardware
---

### Post by ras123 on 2010-07-15
Hi,
How to set up a USB serial port in Ubuntu 10.04?. I had installed all updates currently released, and libftdi and libusb. But when connecting my FT232 based device, it is not listed as /dev/ttyUSB0 

lsusb gives
> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0403:bcda Future Technology Devices International, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubAfter plug-in, tail /var/log/syslog gives (copied only important to USB)
> AptDaemon: INFO: Quiting due to inactivity
AptDaemon: INFO: Shutdown was requested
kernel: [  411.016081] usb 4-3: new full speed USB device using ohci_hcd and address kernel: [  411.194318] usb 4-3: configuration #1 chosen from 1 choice


---

