---
title: "Mitsubishi P95DW custom driver doesn't work on ubuntu 17.01 , works on ubuntu 14.04"
date: 2018-04-13
forum: Hardware
---

### Post by lorenc2 on 2018-04-13
I have a custom driver for Mitsubishi P95DW usb printer as a shared object libp95d.so. This driver uses libusb-0.1.so.4.
This driver works for ubuntu 14.04, kernel (3.19.0-25-generic) but it doesn't work on my new device which runs ubuntu 17.01, kernel (4.13.0-21-generic)

On plugging in the printer I see these messages on dmesg:

[585298.181542] usb 1-3: new high-speed USB device number 14 using ehci-pci
[585298.378174] usb 1-3: New USB device found, idVendor=06d3, idProduct=3b10
[585298.378176] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[585298.378177] usb 1-3: Product: USB PRINTER
[585298.378178] usb 1-3: Manufacturer: MITSUBISHI
[585298.395079] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 14 if 0 alt 0 proto 2 vid 0x06D3 pid 0x3B10

The device is listed on both systems:
$ lsusb
Bus 001 Device 014: ID 06d3:3b10 Mitsubishi Electric Corp.

(on non working system)
$ udevadm info -q all -n /dev/usb/lp0
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/usbmisc/lp0
N: usb/lp0
E: DEVNAME=/dev/usb/lp0
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/usbmisc/lp0
E: MAJOR=180
E: MINOR=0
E: SUBSYSTEM=usbmisc

(on working system)
$ udevadm info -q all -n /dev/usb/lp0
P: /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-3=2:1.0/usbmisc/lp0
N: usb/lp0
E: DEVNAME=/dev/usb/lp0
E: DEVPATH= /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-3=2:1.0/usbmisc/lp0
E: ID_BUS=usb
E: ID_MODEL=USB_PRINTER
E: ID_MODEL_ENC=USB\x20PRINTER
E: ID_REVISION=0100
E: ID_TYPE=printer
E: ID_USB_DRIVER=usblp
E: ID_USB_INTERFACES=:070102
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=MITSUBISHI
E: ID_VENDOR_ENC=MITSUBISHI
E: ID_VENDOR_ID=0643
E: MAJOR=180
E: MINOR=0
E: SUBSYSTEM=usbmisc

I don't know if this difference is important or not.

When I try to print on the new system I get Error_Busy.
This printer driver does not use CUPS.

Any idea on how to investigate the issue?

---

### Post by oldos2er on 2018-04-13
Support, not chat. Moved to Hardware.

---

