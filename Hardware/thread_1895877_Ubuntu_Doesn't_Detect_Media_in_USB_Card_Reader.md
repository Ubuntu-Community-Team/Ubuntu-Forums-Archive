---
title: "Ubuntu Doesn't Detect Media in USB Card Reader"
date: 2011-12-15
forum: Hardware
---

### Post by Destructo47 on 2011-12-15
I have a Digital Concepts CR-75 51-in-1 USB card reader. When I plug it in by itself, I get four new empty partitions that show up (labeled 'Myson'). However, when I insert an SD card or mini SD card into the appropriate slot, the partition where that card would mount at seems to disappear. The other unused ones still show up, but obviously are inaccessible because of lack of media. 
I have the driver disc for Windows, but I can't find Natty drivers anywhere. I might also add that on Windows, the read/write LED lights up after a moment, but on Ubuntu it only gives power to it. XD cards seem to work for some reason.

I also ran into something interesting when booting the GParted Live disc, but I can't recall the error at the moment. I can remember that it shows a timeout error and tries to kill some process, but fails until I remove the device.

This is a serious inconvenience, as I'm making backups of some console games onto my hard drive and transferring files over the router is time-consuming, confusing, and slow. Any help would be much appreciated.

---

### Post by Destructo47 on 2012-10-01
Mega bump. Why do I always seem to get the issues that nobody cares about? I've had at least three individual threads on separate issues that no one has bothered to reply to.

---

### Post by Routhinator on 2013-04-12
> **Destructo47 said:**
> Mega bump. Why do I always seem to get the issues that nobody cares about? I've had at least three individual threads on separate issues that no one has bothered to reply to.

I Second that request. I have the same issue with the same card reader. Not sure what to do here.

Ubuntu 12.10

---

### Post by Routhinator on 2013-04-12
As a follow up I'm doing a little investigating with this.

lsusb output: 

```
Bus 001 Device 004: ID 04cf:9920 Myson Century, Inc. CS8819A2-114 Mass Storage Device
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04cf Myson Century, Inc.
  idProduct          0x9920 CS8819A2-114 Mass Storage Device
  bcdDevice           a3.16
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

This is how the device shows in USB. So it is being picked up, however it does not seem to automount..

---

### Post by Routhinator on 2013-04-12
Finding out a little more about this device..

```
routh@routh-laptop:~$ ls -l /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 Apr 12 15:51 /dev/disk/by-id/usb-Myson_CS8819A3-116_0_100-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 9 Apr 12 15:51 /dev/disk/by-id/usb-Myson_CS8819A3-116_1_100-0:1 -> ../../sdc
lrwxrwxrwx 1 root root 9 Apr 12 15:51 /dev/disk/by-id/usb-Myson_CS8819A3-116_2_100-0:2 -> ../../sdd
lrwxrwxrwx 1 root root 9 Apr 12 15:51 /dev/disk/by-id/usb-Myson_CS8819A3-116_3_100-0:3 -> ../../sde

```

It seems to load 4 virtual hard drives for mounting the cards.. however attempting to them manually tells be that there is no disk on any of them.

---

### Post by Routhinator on 2013-04-12
Going further still, here is the information I managed to get back from udevadm:

```
routh@routh-laptop:/dev$ udevadm info --query=all --name=/dev/sdb
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:0/block/sdb
N: sdb
S: disk/by-id/usb-Myson_CS8819A3-116_0_100-0:0
S: disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
E: DEVLINKS=/dev/disk/by-id/usb-Myson_CS8819A3-116_0_100-0:0 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
E: DEVNAME=/dev/sdb
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:0/block/sdb
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:0
E: ID_MODEL=CS8819A3-116_0
E: ID_MODEL_ENC=CS8819A3-116\x20\x200\x20
E: ID_MODEL_ID=9920
E: ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_1_1_0-scsi-0_0_0_0
E: ID_REVISION=1.01
E: ID_SERIAL=Myson_CS8819A3-116_0_100-0:0
E: ID_SERIAL_SHORT=100
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Myson
E: ID_VENDOR_ENC=Myson\x20\x20\x20
E: ID_VENDOR_ID=04cf
E: MAJOR=8
E: MINOR=16
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=3819149700

routh@routh-laptop:/dev$ udevadm info --query=all --name=/dev/sdc
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:1/block/sdc
N: sdc
S: disk/by-id/usb-Myson_CS8819A3-116_1_100-0:1
S: disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:1
E: DEVLINKS=/dev/disk/by-id/usb-Myson_CS8819A3-116_1_100-0:1 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:1
E: DEVNAME=/dev/sdc
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:1/block/sdc
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:1
E: ID_MODEL=CS8819A3-116_1
E: ID_MODEL_ENC=CS8819A3-116\x20\x201\x20
E: ID_MODEL_ID=9920
E: ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:1
E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_1_1_0-scsi-0_0_0_1
E: ID_REVISION=1.01
E: ID_SERIAL=Myson_CS8819A3-116_1_100-0:1
E: ID_SERIAL_SHORT=100
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Myson
E: ID_VENDOR_ENC=Myson\x20\x20\x20
E: ID_VENDOR_ID=04cf
E: MAJOR=8
E: MINOR=32
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=3820062909

routh@routh-laptop:/dev$ udevadm info --query=all --name=/dev/sdd
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:2/block/sdd
N: sdd
S: disk/by-id/usb-Myson_CS8819A3-116_2_100-0:2
S: disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:2
E: DEVLINKS=/dev/disk/by-id/usb-Myson_CS8819A3-116_2_100-0:2 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:2
E: DEVNAME=/dev/sdd
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:2/block/sdd
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:2
E: ID_MODEL=CS8819A3-116_2
E: ID_MODEL_ENC=CS8819A3-116\x20\x202\x20
E: ID_MODEL_ID=9920
E: ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:2
E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_1_1_0-scsi-0_0_0_2
E: ID_REVISION=1.01
E: ID_SERIAL=Myson_CS8819A3-116_2_100-0:2
E: ID_SERIAL_SHORT=100
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Myson
E: ID_VENDOR_ENC=Myson\x20\x20\x20
E: ID_VENDOR_ID=04cf
E: MAJOR=8
E: MINOR=48
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=3820073661

routh@routh-laptop:/dev$ udevadm info --query=all --name=/dev/sde
P: /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:3/block/sde
N: sde
S: disk/by-id/usb-Myson_CS8819A3-116_3_100-0:3
S: disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:3
E: DEVLINKS=/dev/disk/by-id/usb-Myson_CS8819A3-116_3_100-0:3 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:3
E: DEVNAME=/dev/sde
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host9/target9:0:0/9:0:0:3/block/sde
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:3
E: ID_MODEL=CS8819A3-116_3
E: ID_MODEL_ENC=CS8819A3-116\x20\x203\x20
E: ID_MODEL_ID=9920
E: ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:3
E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_1_1_0-scsi-0_0_0_3
E: ID_REVISION=1.01
E: ID_SERIAL=Myson_CS8819A3-116_3_100-0:3
E: ID_SERIAL_SHORT=100
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Myson
E: ID_VENDOR_ENC=Myson\x20\x20\x20
E: ID_VENDOR_ID=04cf
E: MAJOR=8
E: MINOR=64
E: SUBSYSTEM=block
E: UDEV_LOG=3
E: UDISKS_PRESENTATION_NOPOLICY=0
E: USEC_INITIALIZED=3820071891

routh@routh-laptop:/dev$ 

```

---

