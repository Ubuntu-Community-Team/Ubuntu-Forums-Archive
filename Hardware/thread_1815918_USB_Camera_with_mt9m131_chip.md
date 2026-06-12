---
title: "USB Camera with mt9m131 chip"
date: 2011-08-01
forum: Hardware
---

### Post by matthez on 2011-08-01
Hi there,

I have a USB Cam with a Micron mt9m131 Chip (written in the Datasheet). After plugin i didn't get a /dev/video0. My kernel is Linux version 2.6.38-10-generic.

on lsusb i get:
```
Bus 001 Device 004: ID 0547:6131 Anchor Chips, Inc. 
```hwinfo:
```

07: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: X7GA.KJK2b4TOcM5
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0
  SysFS BusID: 1-7:1.0
  Hardware Class: unknown
  Model: "Anchor Chips 1.3M USBCAM"
  Hotplug: USB
  Vendor: usb 0x0547 "Anchor Chips, Inc."
  Device: usb 0x6131 "1.3M USBCAM"
  Speed: 480 Mbps
  Module Alias: "usb:v0547p6131d0000dc00dsc00dp00icFFisc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #2 (Hub)

```with dmesg:
```
[   93.448097] usb 1-7: new high speed USB device using ehci_hcd and address 4
[   94.008559] usb 1-7: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 9

```Here i found that this chip should be supported: [http://kernel.xc.net/html/linux-2.6.38/xtensa/SOC_CAMERA_MT9M111](http://kernel.xc.net/html/linux-2.6.38/xtensa/SOC_CAMERA_MT9M111).

My problem i don't kown how to do. I tried modprobe mt9m111 but it notify "No such device".
I need help.
Thanks

---

### Post by matthez on 2011-08-01
Okay, further I figured out, the driver is for a I2C connection.
The Chip is connected internaly via I2C to USB to Ubuntu.
Any Ideas how to get the Cam working?

---

