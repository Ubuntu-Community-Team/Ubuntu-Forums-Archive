---
title: "udev rule not working"
date: 2015-08-22
forum: Hardware
---

### Post by malaTG on 2015-08-22
Hi

I created a new udev rule but it is not working for my scanner. I have some other rules that works perfectly. Could someone help me on how to trace down the issue?

My udev rule file

```
# add master-of-seat tag to video cards (0x10de is NVIDIA vendor id)
SUBSYSTEM=="drm", KERNEL=="card[0-9]*", ATTRS{vendor}=="0x10de", DRIVERS=="nvidia", TAG+="master-of-seat"

# assign USB ports
TAG=="seat", DEVPATH=="/devices/pci0000:00/0000:00:1d.0/usb6/6-2/*", ENV{ID_SEAT}="seat-1", TAG+="seat-1"
TAG=="seat", DEVPATH=="/devices/pci0000:00/0000:00:1d.0/usb6/6-1/*", ENV{ID_SEAT}="seat-1", TAG+="seat-1"
TAG=="seat", DEVPATH=="/devices/pci0000:00/0000:00:1a.2/usb5/5-2/*", ENV{ID_SEAT}="seat-1", TAG+="seat-1"
TAG=="seat", ID_MODEL=="EPSON_Scanner", ENV{ID_SEAT}="seat-1", TAG+="seat-1"

# assign video cards
#TAG=="seat", DEVPATH=="/devices/pci0000:00/0000:00:1e.0/0000:07:02.0/*", ENV{ID_SEAT}="seat-1", TAG+="seat-1"
TAG=="seat", DEVPATH=="/devices/pci0000:00/0000:00:01.0/0000:01:00.0/*", ENV{ID_SEAT}="seat-1", TAG+="seat-1"

```

Output from the command "udevadm info --export-db | grep -A 30 -B 30 EPSON_Scanner"

```
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-2
N: bus/usb/001/003
E: BUSNUM=001
E: DEVNAME=/dev/bus/usb/001/003
E: DEVNUM=003
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-2
E: DEVTYPE=usb_device
E: DRIVER=usb
E: ID_BUS=usb
E: ID_FOR_SEAT=usb-pci-0000_00_1a_7-usb-0_2
E: ID_MODEL=EPSON_Scanner
E: ID_MODEL_ENC=EPSON\x20Scanner
E: ID_MODEL_FROM_DATABASE=GT-X770 [Perfection V500]
E: ID_MODEL_ID=0130
E: ID_PATH=pci-0000:00:1a.7-usb-0:2
E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_2
E: ID_REVISION=0100
E: ID_SERIAL=EPSON_EPSON_Scanner
E: ID_USB_INTERFACES=:ffffff:
E: ID_VENDOR=EPSON
E: ID_VENDOR_ENC=EPSON
E: ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
E: ID_VENDOR_ID=04b8
E: MAJOR=189
E: MINOR=2
E: PRODUCT=4b8/130/100
E: SUBSYSTEM=usb
E: TAGS=:seat:uaccess:
E: TYPE=255/255/255
E: USEC_INITIALIZED=74996
E: libsane_matched=yes

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
E: DEVTYPE=usb_interface
E: ID_MODEL_FROM_DATABASE=GT-X770 [Perfection V500]
E: ID_USB_CLASS_FROM_DATABASE=Vendor Specific Class
E: ID_USB_PROTOCOL_FROM_DATABASE=Vendor Specific Protocol
E: ID_USB_SUBCLASS_FROM_DATABASE=Vendor Specific Subclass
E: ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
E: INTERFACE=255/255/255
E: MODALIAS=usb:v04B8p0130d0100dcFFdscFFdpFFicFFiscFFipFFin00
E: PRODUCT=4b8/130/100
E: SUBSYSTEM=usb
E: TYPE=255/255/255
E: USEC_INITIALIZED=22734

```

As you can see the scanner is not tagged with "seat-1"!?

---

### Post by malaTG on 2015-08-23
Problem solved. Must have been tired yesterday :-) Anyway the correct line is...

TAG=="seat", ATTRS{idVendor}=="04b8", ENV{ID_SEAT}="seat-1", TAG+="seat-1"

---

