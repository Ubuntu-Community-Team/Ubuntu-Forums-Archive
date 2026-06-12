---
title: "Wake on USB Zotac"
date: 2015-04-05
forum: Hardware
---

### Post by miguel37 on 2015-04-05
I have been trying to get my wake on USB working on my zotac but with no luck.

I am trying to wake up from suspend from a USB keyboard. I am running Ubuntu 14.04.1 (KODIBUNTU)
[PHP]lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 20a0:0001 Clay Logic
Bus 003 Device 006: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 2109:0811
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

[PHP]lsusb -t
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 2: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 2: Dev 5, If 1, Class=Vendor Specific Class, Driver=, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M
[/PHP]

[PHP]cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
P0P1      S4    *disabled  pci:0000:00:1e.0
P0P4      S4    *disabled  pci:0000:00:1c.0
P0P5      S4    *disabled  pci:0000:00:1c.1
P0P6      S4    *disabled  pci:0000:00:1c.2
P0P7      S4    *disabled
P0P8      S4    *disabled
P0P9      S4    *disabled
USB0      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *enabled   pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USB3      S3    *enabled   pci:0000:00:1d.3
EUSB      S3    *enabled   pci:0000:00:1d.7
[/PHP]

The Keyboard is plugged into Bus 3 Device 6 based on the lsusb -t command I need to enable wakeup on Bus 3 Port 1 to do this I run the following command...

[PHP]echo enabled > /sys/bus/usb/devices/3-1/power/wakeup
[/PHP]

I  then confirm that wakeup is enabled on Bus 3 Port 1

[PHP][root@xbmc:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/power# cat /sys/bus/usb/devices/3-1/power/wakeup
enabled
[/PHP]

However I seem to have missed something because the keyboard doesn't wake up the system on suspend I think any assistance would be appreciate to get wake on usb working.

---

