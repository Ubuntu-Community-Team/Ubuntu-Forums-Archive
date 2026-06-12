---
title: "Ubuntu Live USB device does not mount and connot be seen in /dev"
date: 2013-03-06
forum: Hardware
---

### Post by defmer on 2013-03-06
So I created a startup USB device using the "startup disk creator". I used it to install it on a host and now I cannot seem to mount it or use it anymore. I cannot get a /dev partition for it. When I plug in, I see the following in the DMESG:

[ 3553.452044] usb 2-2: new high-speed USB device number 3 using ehci_hcd
[ 3553.584436] usb 2-2: New USB device found, idVendor=1307, idProduct=0163
[ 3553.584442] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 3553.584867] scsi9 : usb-storage 2-2:1.0
[ 3554.584703] scsi 9:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 3554.585342] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 3554.589045] sd 9:0:0:0: [sdb] Attached SCSI removable disk

In "lsusb" it is shown as : Bus 002 Device 003: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive

and lsusb -v gives this message:
Bus 002 Device 003: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1307 Transcend Information, Inc.
  idProduct          0x0163 256MB/512MB/1GB Flash Drive
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
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
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
Device Status:     0xde30
  (Bus Powered)


So how should a I proceed further???????

---

