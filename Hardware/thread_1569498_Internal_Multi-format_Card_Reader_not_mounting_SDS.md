---
title: "Internal Multi-format Card Reader not mounting SD/SDHC"
date: 2010-09-06
forum: Hardware
---

### Post by mfdc1969 on 2010-09-06
My desktop has a multi-format card reader in the 3.5 bay which is connected via USB2 to the mainboard:

[INDENT]ATECH FLASH TECHNOLOGY
PRO-Gear XM-4U
717670857912
[http://www.atechflash.com/products-pgxm4u.html]("http://www.atechflash.com/products-pgxm4u.html")[/INDENT]

The USB connector works to connect my MP3 player, it mounts CF cards but it will not mount SD/SDHC cards.

Here are results of my looking under the hood, based on what I have gleaned from other related posts:

**$ sudo lsusb -vv**

```
Bus 001 Device 003: ID 11b0:6566 ATECH FLASH TECHNOLOGY 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x11b0 ATECH FLASH TECHNOLOGY
  idProduct          0x6566 
  bcdDevice            1.00
  iManufacturer           1 Atech Flash
  iProduct                2 PRO-Gear XM-4U
  iSerial                 4 717670857912
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              498mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

**$ lshal | grep SD**
```

scsi.model = 'CardReader SD'  (string)
udi = '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_SD_717670857912_0_3'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_SD_717670857912_0_3'  (string)
  info.product = 'CardReader SD'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_SD_717670857912_0_3'  (string)
  storage.model = 'CardReader SD'  (string)
  storage.serial = 'USB2.0_CardReader_SD_717670857912-0:3'  (string)
```

Can someone please suggest where to turn next?

---

### Post by mfdc1969 on 2010-09-11
Any suggestions folks?

Is this just a simple hard ware failure or ... ?

---

### Post by efflandt on 2010-09-11
What does the tail end of dmesg show after inserting SD or SDHC?  What partition(s) or file system is on the memory?

Card readers built into laptops are typically some other type of block device, but card readers connected by usb are usually easily recognized as usb mass storage.

Do you get any errors in dmesg (or /var/log/messages) trying to read a non-existing floppy drive?  I had that issue that prevented auto mounting usb or optical disks (CD/DVD) on a laptop with a hot swap drive bay.  Since that laptop normally had no floppy, I had to blacklist floppy and **sudo update-initramfs -u** so the floppy module would not load during boot.

---

### Post by mfdc1969 on 2010-09-28
Sorry for the late reply ... kids, the start of school - etc!

There is no message from dmesg or /var/log/messages that relates to the SD or SDHC card reader or any other USB device. 

The card is from my Nikon D5000 digital camera and is filesystem type: msdos.

The SDHC card auto-mounts and reads perfectly in my laptop Acer 5610Z with internal card reader which is running Edubuntu/Ubuntu 10.04. Therefore I believe the file system is not an issue.

Could this simply be a hardware issue?

---

### Post by frankvdh on 2010-09-29
I have had a similar (but different) problem for some time. I think it is something to do with deleting files on a USB device from Ubuntu... that's when everything seems to go haywire. This seems to happen on several different devices (e.g. my GPS) as well as card readers.

For example, I presently have an AVLABS 70-in-1 USB card reader plugged into a hub. This works fine in WinXP (AFAICT... I don't use WinXP much), and sometimes works OK in Ubuntu 10.4. I have a 16GB SDHC card plugged into the reader

At the moment it isn't working... there are no devices visible in Ubuntu.

Tail end of dmesg looks like this:

[ 1012.840249] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1012.840255]    : Sense Key : Hardware Error [current] 
[ 1012.840261]    : Add. Sense: No additional sense information
[ 1012.850750] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1012.850756]    : Sense Key : Hardware Error [current] 
[ 1012.850762]    : Add. Sense: No additional sense information
[ 1014.840486] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1014.840492]    : Sense Key : Hardware Error [current] 
[ 1014.840525]    : Add. Sense: No additional sense information
[ 1014.851617] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1014.851624]    : Sense Key : Hardware Error [current] 
[ 1014.851633]    : Add. Sense: No additional sense information
[ 1016.838722] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1016.838728]    : Sense Key : Hardware Error [current] 
[ 1016.838735]    : Add. Sense: No additional sense information
[ 1016.849348] sd 4:0:0:2: ioctl_internal_command return code = 8070000
[ 1016.849353]    : Sense Key : Hardware Error [current] 
[ 1016.849360]    : Add. Sense: No additional sense information

lsusb gives me:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04cf:8819 Myson Century, Inc. 
Bus 001 Device 006: ID eb1a:2861 eMPIA Technology, Inc. 
Bus 001 Device 005: ID 1941:8021 Dream Link USB Missile Launcher
Bus 001 Device 003: ID 05e3:0660 Genesys Logic, Inc. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The "Myson Century, Inc" device is in fact the USB card reader.

---

### Post by mfdc1969 on 2010-11-21
OK, all solved - it was a hardware issue. I replaced teh offending part with a new [Card Reader]("http://www.rocketfishproducts.com/products/computers/RF-CRDRD.html") and it is working again! Thanks for helping me folks!

---

