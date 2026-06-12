---
title: "Mount USBIP Thumbdrive"
date: 2018-04-26
forum: Hardware
---

### Post by houndnews on 2018-04-26
Have searched forum but without luck.  Running Odroid xu4 server with 4.14.35+ kernel Ubuntu 16.04 recompile to include usbip.  Linux-tools.4.15.0-15-generic installed.  Have successfully bound to PNY usb stick.  Client side is desktop Ubuntu 16.04 with  4.13.0-39-generic kernel and same version 4.15 of linux-tools-generic.installed.  Have been able to attach remote usb device.
  
Lsusb shows Bus 004 Device 002: ID 154b:00d2 PNY ,

 lshw shows 

 *-usbhost:0
       product: USB/IP Virtual Host Controller
       vendor: Linux 4.13.0-39-generic vhci_hcd
       physical id: 2
       bus info: usb@3
       logical name: usb3
       version: 4.13
       capabilities: usb-2.00
       configuration: driver=hub slots=8 speed=480Mbit/s
  *-usbhost:1
       product: USB/IP Virtual Host Controller
       vendor: Linux 4.13.0-39-generic vhci_hcd
       physical id: 3
       bus info: usb@4
       logical name: usb4
       version: 4.13
       capabilities: usb-3.00
       configuration: driver=hub slots=8 speed=5000Mbit/s
     *-usb
          description: Mass storage device
          product: USB 3.0 FD
          vendor: PNY
          physical id: 1
          bus info: usb@4:1
          version: 1.00
          serial: 070A6A305FDF1597
          capabilities: usb-3.10 scsi
          configuration: driver=usb-storage maxpower=504mA speed=5000Mbit/s
  *-scsi
       physical id: 4
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

Have created a mount point /media/usbstick.  Have tried many variations of mount -t fstype /... /media/usbstick but am unable to mount device.  Keep getting error special device not present or words to that effect. Have tried a different stick same results. Tried a webcam which is detected and guvcview launches with video window but no video.  Any advice on how to mount this detected thumbdrive or webcam.  TIA

---

