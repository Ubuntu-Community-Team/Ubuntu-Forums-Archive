---
title: "How to treat unknown hardware?"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by ofir_k on 2008-04-06
Hello,

I recently purchased some device called "Photo Viewer". It displays pictures (like a picture frame).

Anyway, this device requires a software to transfer images to it. There isn't a version for linux, so the only way is to try tell ubuntu how to handle it.

When running ` sudo lsusb -s 003:003 -v` it outputs:
```
Bus 003 Device 003: ID 1403:0001  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1403 
  idProduct          0x0001 
  bcdDevice            1.10
  iManufacturer           1 
  iProduct                2 Flash Disk      
  iSerial                 0 
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
    MaxPower              100mA
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
Device Status:     0x0000
  (Bus Powered)

```

I am not an expert. however, it seems to me that this device is a regular mass storage...

Is there an option (if it acts like a Disk-on-key) to tell Ubuntu how to handle it?

Ofir

P.S
If you think that this is not possible, please post.

---

### Post by chewearn on 2008-04-07
If it is acting like a regular mass storage, it should show up under /media/ (with link on desktop) after you plug it in.  Did that happen?

---

### Post by ofir_k on 2008-04-08
No. It didn't happen.

The Device Manager indicates that this device uses SD:
info.linux.driver   string  sd

It recognize it as Flash Disk, and the device is placed in /dev/sdb

Is there a way to mount it? I don't know which filesystem SD is considered.

P.S
The 'tree' in the Device Manager is as follows:
Flash Disk
  USB Mass Storage Interface
    SCSI Host Adapter
      SCSI Device
        MULTIMEDIA
        SCSI Generic Interface

---

### Post by chewearn on 2008-04-08
If you are talking about SD, as in Secure Digital:
[http://en.wikipedia.org/wiki/Secure_Digital_card](http://en.wikipedia.org/wiki/Secure_Digital_card)

it should usually be FAT filesystem.  however, if you have /dev/sdb only, but not /dev/sdb1 as well, it looks to be un-partitioned.

Do you see anything from dmesg output?

---

### Post by ofir_k on 2008-04-08
dmesg output when connecting the device:
```
[57350.356000] usb 4-1: USB disconnect, address 2
[57374.384000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[57374.568000] usb 4-1: configuration #1 chosen from 1 choice
[57374.572000] scsi5 : SCSI emulation for USB Mass Storage devices
[57374.572000] usb-storage: device found at 3
[57374.572000] usb-storage: waiting for device to settle before scanning
[57377.216000] usb 1-1: reset low speed USB device using uhci_hcd and address 3
[57379.572000] usb-storage: device scan complete
[57379.576000] scsi 5:0:0:0: Direct-Access     SITRONIX MULTIMEDIA       0.09 PQ: 0 ANSI: 0 CCS
[57379.580000] sd 5:0:0:0: [sdb] 4096 512-byte hardware sectors (2 MB)
[57379.584000] sd 5:0:0:0: [sdb] Write Protect is off
[57379.584000] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[57379.584000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[57379.592000] sd 5:0:0:0: [sdb] 4096 512-byte hardware sectors (2 MB)
[57379.596000] sd 5:0:0:0: [sdb] Write Protect is off
[57379.596000] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[57379.596000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[57379.596000]  sdb: unknown partition table
[57379.624000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[57379.624000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

It seems to be un-partitioned. What should I do then?

---

### Post by chewearn on 2008-04-08
Does the photo frame already working now?  I.e. is it already has some pictures in it, and displaying them?

I'm not sure if the device might be using a proprietary / custom filesystem, which if you tamper with it (by formatting to FAT), you might break it.  Any indication on the user manual about this?  The manufacturer website?

---

### Post by ofir_k on 2008-04-08
It seems that this device is broken.

I tested it under Windows with the provided software and it didn't work...

Anyway, thanks for your help!

---

### Post by Offoffoff on 2008-07-07
I have bought the same thing. It works only in Windows with special program, that puts photos into the device. I sent letter to the device' developers for getting file system specs. I hope they are innovative and treat Open Source well.

---

