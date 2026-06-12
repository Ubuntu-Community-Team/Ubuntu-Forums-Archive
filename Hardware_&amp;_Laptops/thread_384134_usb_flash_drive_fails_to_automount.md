---
title: "usb flash drive fails to automount"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by mr.v. on 2007-03-14
Hi all--

I needed to install a later kernel for a particular device driver. Anyway, I compiled 2.6.20 and all is okay except that when I plug in a usb flash-drive I don't get it to automatically mount and dump an icon on the desktop anymore.

Just fyi, it will mount if I manually type pmount /dev/sdb  (sda is my sata hd. sdb is the flashdrive). However, I still won't see an icon on the desktop. I can access it in /media/sdb and see the files on the flash drive / pen drive

Udev is also properly reporting the events. ```
sudo udevmonitor
``` prints the following when I plug in the flashdrive and pull it back out again:
```

udevmonitor prints the received event from the kernel [UEVENT]
and the event which udev sends out after rule processing [UDEV]

UEVENT[1173859790.029010] add@/devices/pci0000:00/0000:00:0b.0/usb2/2-8
UEVENT[1173859790.029075] add@/class/usb_endpoint/usbdev2.9_ep00
UEVENT[1173859790.032122] add@/devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0
UEVENT[1173859790.032144] add@/class/scsi_host/host8
UEVENT[1173859790.032158] add@/class/usb_endpoint/usbdev2.9_ep03
UEVENT[1173859790.032172] add@/class/usb_endpoint/usbdev2.9_ep83
UEVENT[1173859790.032184] add@/class/usb_device/usbdev2.9
UEVENT[1173859795.046103] add@/devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0/host8/target8:0:0/8:0:0:0
UEVENT[1173859795.046141] add@/class/scsi_disk/8:0:0:0
UEVENT[1173859795.108219] add@/block/sdb
UEVENT[1173859795.108250] add@/class/scsi_device/8:0:0:0
UEVENT[1173859795.108263] add@/class/scsi_generic/sg1
UEVENT[1173859805.375111] remove@/class/usb_endpoint/usbdev2.9_ep03
UEVENT[1173859805.375147] remove@/class/usb_endpoint/usbdev2.9_ep83
UEVENT[1173859805.375161] remove@/class/scsi_generic/sg1
UEVENT[1173859805.375174] remove@/class/scsi_device/8:0:0:0
UEVENT[1173859805.375187] remove@/class/scsi_disk/8:0:0:0
UEVENT[1173859805.375200] remove@/block/sdb
UEVENT[1173859805.375212] remove@/devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0/host8/target8:0:0/8:0:0:0
UEVENT[1173859805.375226] remove@/class/scsi_host/host8
UEVENT[1173859805.375239] remove@/devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0
UEVENT[1173859805.375252] remove@/class/usb_device/usbdev2.9
UEVENT[1173859805.375265] remove@/class/usb_endpoint/usbdev2.9_ep00
UEVENT[1173859805.375278] remove@/devices/pci0000:00/0000:00:0b.0/usb2/2-8
```
even more bizarre, ps -A shows gnome-volume-manager, dbus, udev, and hal all running. I cannot for the life of me figure out what more I need to do...
is the 2.6.20 kernel messages incompatible with previous versions of dbus/udev/&hal ???

Thanks for the help!

---

