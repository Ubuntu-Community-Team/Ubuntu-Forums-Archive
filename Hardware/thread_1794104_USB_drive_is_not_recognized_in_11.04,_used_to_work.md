---
title: "USB drive is not recognized in 11.04, used to work before"
date: 2011-06-30
forum: Hardware
---

### Post by tucemiux on 2011-06-30
On my htc mogul phone there is a utility called nueUSB that lets me use my SD card as a USB hard drive.  Once I connect my phone to a computer the utility pops up asking me if I want to connect  through ActiveSync or as a Mass Storage card.  It used to work on previous versions of ubuntu but I'm trying on 11.04 and the SD card does not get mounted again, it's not even recognized, sudo fdisk -l doesn't show the SD card.

This is the output of sudo fdisk -l, I have 2 hard drives, one IDE, and another on the DVD slot, using a SATA HD: 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7fe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   83  Linux

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15201   122102001    b  W95 FAT32
/dev/sda2           15202       15462     2091008   82  Linux swap / Solaris
/dev/sda3           15462       15475      102400   83  Linux
/dev/sda4           15475       30402   119902208    5  Extended
/dev/sda5           15475       18036    20573184   83  Linux
/dev/sda6           18036       27780    78270464   83  Linux

The device is not recognized but lsusb detects it:

Bus 005 Device 007: ID 0bb4:0c13 High Tech Computer Corp

How do I load the drivers for the device?  Ubuntu 11.04 broke on me and no longer supports this functionality on my phone.

---

### Post by tucemiux on 2011-07-07
Anyone knows how to figure out what drivers a device uses, where to find the drivers, and how install and configure the drivers?  The drivers exist, they used to be installed on ubuntu and worked out of the box.  I upgraded to 11.04 using an ISO and now my USB storage device doesn't work anymore.

sudo lsusb -v

Bus 005 Device 018: ID 0bb4:0c13 High Tech Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x0c13 
  bcdDevice            0.00
  iManufacturer           1 Wei Enterprises
  iProduct                2 Storage
  iSerial                 3 3fbf5000-7351-0801-3336-354444373741
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

---

### Post by tucemiux on 2011-07-18
I updated my laptop.  It seems the updates fixed this, now the drive gets mounted automatically.

---

