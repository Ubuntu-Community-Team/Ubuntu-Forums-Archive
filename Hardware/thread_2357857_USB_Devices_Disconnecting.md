---
title: "USB Devices Disconnecting"
date: 2017-04-06
forum: Hardware
---

### Post by jsuiker on 2017-04-06
I am a newcomer to the ubuntu desktop environment.  Having reached my  threshold for the number of times I have to reinstall Windows and futz  with their licensing BS, I've finally decided to make the jump to a  linux environment.  

Most importantly, I've been developing some software that relies heavily  on hardware such as printers and barcode scanners. I'd like to put  together a package that works with ubuntu so that my clients don't have  to worry about Microsoft licensing issues either.

I'm having some issues with a few of these USB devices, though. One is a  Motorola (Zebra) scanner and one is a Zebra label printer.  It seems  that whenever the computer tries to print or the scanner tries to read  in a barcode, the device is disconnected for whatever reason and  re-connect shortly thereafter.

I am running Ubuntu 16.10 on an Optiplex 9020

$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/15p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 3: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 5: Dev 13, If 0, Class=Printer, Driver=usblp, 12M                                         <==== Zebra LP2824 Printer (VID  0x0a5f PID 0x0015)
        |__ Port 6: Dev 5, If 0, Class=Hub, Driver=hub/3p, 480M
            |__ Port 3: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            |__ Port 3: Dev 8, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
            |__ Port 1: Dev 6, If 0, Class=Hub, Driver=hub/3p, 480M
                |__ Port 1: Dev 9, If 0, Class=Mass Storage, Driver=usb-storage, 480M
                |__ Port 2: Dev 14, If 0, Class=Human Interface Device,  Driver=usbhid, 12M    <==== Symbol DS6708 Scanner ( VID 0x05e0 PID  0x1300)
            |__ Port 2: Dev 7, If 1, Class=Human Interface Device, Driver=usbhid, 12M
            |__ Port 2: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M


::: SCANNER IN HID RAW MODE :::


dmesg -w (while scanning a barcode)

[  919.541217] usb 2-1.6.1.2: USB disconnect, device number 12
[  919.908374] usb 2-1.6.1.2: new full-speed USB device number 14 using ehci-pci
[  920.022163] usb 2-1.6.1.2: New USB device found, idVendor=05e0, idProduct=1300
[  920.022165] usb 2-1.6.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  920.022166] usb 2-1.6.1.2: Product: Symbol Bar Code Scanner
[  920.022167] usb 2-1.6.1.2: Manufacturer: &#65449;Symbol Technologies, Inc, 2002
[  920.022167] usb 2-1.6.1.2: SerialNumber: S/N:63FC61BF9E8E2247B78E81D22AF2F5E7 Rev:NBRPPAAP1
[  920.026114] hid-generic 0003:05E0:1300.0009: hiddev0,hidraw6: USB HID  v1.10 Device [&#65449;Symbol Technologies, Inc, 2002 Symbol Bar Code Scanner]  on usb-0000:00:1d.0-1.6.1.2/input0

::: PRINTING A TEST PAGE :::

dmesg -w (while trying to print a test page)

[  959.983017] usblp0: removed
[  963.256150] usblp 2-1.5:1.0: usblp0: USB Bidirectional printer dev 13 if 0 alt 0 proto 2 vid 0x0A5F pid 0x0015

---

