---
title: "Photo transfer from Samsung SCH-U640 to ubuntu"
date: 2011-02-07
forum: Hardware
---

### Post by billmania on 2011-02-07
I have a Lenovo R61e, 7650-84u, running 32 bit ubuntu 10.04.2 LTS. I would like to transfer photos from a Samsung SCH-U640 mobile phone (Qualcomm) with USB vendor and product ID 05c6:1000. The Samsung phone is in media sync mode. The phone is not being recognized by the OS. How do I transfer photos from the phone to the computer?


The output of "lsusb -vv", when the phone is connected to the notebook computers, is:

Bus 005 Device 004: ID 05c6:1000 Qualcomm, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x1000
  bcdDevice            0.00
  iManufacturer           1 Qualcomm, Incorporated
  iProduct                2 USB Mass Storage
  iSerial                 3 000000000002
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
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

The output of "dmesg -" is:

[   73.552075] usb 5-1: new full speed USB device using uhci_hcd and address 4
[   73.713044] usb 5-1: configuration #1 chosen from 1 choice
[   73.719518] scsi6 : SCSI emulation for USB Mass Storage devices
[   73.719723] usb-storage: device found at 4
[   73.719725] usb-storage: waiting for device to settle before scanning


brw-rw----  1 root disk   8,  0 2011-02-07 20:20 /dev/sda
brw-rw----  1 root disk   8,  1 2011-02-07 20:20 /dev/sda1
brw-rw----  1 root disk   8,  2 2011-02-07 20:20 /dev/sda2
brw-rw----  1 root disk   8,  5 2011-02-07 20:20 /dev/sda5
brw-rw----  1 root disk   8, 16 2011-02-07 20:20 /dev/sdb
brw-rw----+ 1 root cdrom 11,  0 2011-02-07 20:20 /dev/sr0

/dev/sda1 on / type ext4 (rw,errors=remount-ro)

---

### Post by billmania on 2011-02-07
Also:

usbserial              33019  4 option
usb_storage            39553  0

---

### Post by billmania on 2011-02-07
This is what appears in /var/log/messages when the phone is connected via USB:

Feb  7 20:55:53 jim-notebook kernel: [ 2156.556065] usb 5-1: new full speed USB device using uhci_hcd and address 5
Feb  7 20:55:53 jim-notebook kernel: [ 2156.713397] usb 5-1: configuration #1 chosen from 1 choice
Feb  7 20:55:53 jim-notebook kernel: [ 2156.716654] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Feb  7 20:55:54 jim-notebook kernel: [ 2157.768140] usb 5-1: USB disconnect, address 5
Feb  7 20:55:56 jim-notebook kernel: [ 2159.040064] usb 5-1: new full speed USB device using uhci_hcd and address 6
Feb  7 20:55:56 jim-notebook kernel: [ 2159.200804] usb 5-1: configuration #1 chosen from 1 choice
Feb  7 20:55:56 jim-notebook kernel: [ 2159.207304] scsi7 : SCSI emulation for USB Mass Storage devices

---

### Post by billmania on 2011-02-19
I have upgraded this machine to ubuntu 32 bit desktop 10.10 now. The results are still the same. The phone's collection of photos is not automatically mounted.
How do I cause the phone's filesystem to be automatically mounted on the computer?

---

### Post by Sam Lars on 2011-05-29
I have the same phone, another post here referred to this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329)

---

