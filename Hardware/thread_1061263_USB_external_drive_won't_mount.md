---
title: "USB external drive won't mount"
date: 2009-02-05
forum: Hardware
---

### Post by seedsgrow on 2009-02-05
I have a USB drive that will now longer mount. It still mounts in OpenSuSE 11.0, which is built on kernel 2.6.25, but it will not mount in Ubuntu 8.10 or four other distributions that are built on kernel 2.6.27. All of my other USB devices mount in all the distributions I currently use or have recently tested.

Here is the info from hwinfo:

UDI: /org/freedesktop/Hal/devices/usb_device_4971_a002_8F29E2_if0_scsi_host_0_scsi_device_lun0_scsi_generic
  Unique ID: CLb3.vQ_wcuH+9uD
  SysFS ID: /class/block/sdb
  SysFS BusID: 5:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6.5/7-6.5:1.0/host5/target5:0:0/5:0:0:0
  Hardware Class: disk
  Model: "WDC WD16 00BB-56GUC0"
  Vendor: usb 0x4971 "WDC WD16"
  Device: usb 0xa002 "00BB-56GUC0"
  Revision: "20.0"
  Serial ID: "8F29E2"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdb (/dev/sg2)
  Device Number: block 8:16-8:31 (char 21:2)
  Speed: 480 Mbps
  Module Alias: "usb:v4971pA002d0001dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: libusual is active
    Driver Activation Cmd: "modprobe libusual"
  Drive status: no medium


The lsusb information for this device is:

Bus 007 Device 004: ID 4971:a002.


When I run a blkid command, no UUID id displayed for this drive.

Any ideas anyone?

---

### Post by taurus on 2009-02-05
Does it even show up from the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by seedsgrow on 2009-02-06
[I]Does it even show up from the output of this command from a terminal?

Code:

sudo fdisk -l[/I]


No, it does not.

---

### Post by seedsgrow on 2009-02-06
I guess I'd still like ideas about why this device won't mount in any of the new distros via the USB 2.0 connection. I'm thinking it may be some kind of kernel-level bug. Anyway, this external drive also has a Firewire interface. I needed to get a cable with a 4-circuit plug on one end before I could test if I could get the drive to mount using it. I just got one and found that the drive works fine using a Firewire connection.

---

