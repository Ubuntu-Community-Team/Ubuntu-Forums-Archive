---
title: "Error with Nokia 6300 as gsm modem"
date: 2009-09-23
forum: Hardware
---

### Post by wollecni74 on 2009-09-23
Hello,
 
i have got an issue with my Nokia 6300. When i connect the device with the USB cable, it works for a couple of hours and i can sent an sms with command: "gsmsendsms -d /dev/ttyACM0 +31612345678 test".
 
After a while i get an error: "[COLOR=#333333][FONT=Lucida Sans Unicode][SIZE=1]gsmsendsms[ERROR]: opening device '/dev/ttyACM0' (errno: 5/Input/output error)[/SIZE][/FONT][/COLOR]"
 
lsusb shows the following:
Bus 001 Device 011: ID 0421:04f9 Nokia Mobile Phones 6300 (PC-Suite mode)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsusb -d 0421:04f9 -v shows:
Bus 001 Device 011: ID 0421:04f9 Nokia Mobile Phones 6300 (PC-Suite mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0421 Nokia Mobile Phones
  idProduct          0x04f9 6300 (PC-Suite mode)
  bcdDevice            7.00
  iManufacturer           1 Nokia
  iProduct                2 Nokia 6300
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          478
    bNumInterfaces         15
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass      8 Wireless Handset Control
      bInterfaceProtocol      1
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      INVALID CDC (Telephone Operations):  05 24 08 00 01
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 2 3 4 5 6 7 8 9 10 11 12 13 14
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      CDC ACM:
        bmCapabilities       0x06
          sends break
          line coding and serial state
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          2
      CDC Union:
        bMasterInterface        1
        bSlaveInterface         2
      UNRECOGNIZED CDC:  04 24 fd 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass     11 OBEX
      bInterfaceProtocol      0
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      CDC OBEX:
        bcdVersion           1.00
      CDC Union:
        bMasterInterface        3
        bSlaveInterface         4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass     11 OBEX
      bInterfaceProtocol      0
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      CDC OBEX:
        bcdVersion           1.00
      CDC Union:
        bMasterInterface        5
        bSlaveInterface         6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 00
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
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        7
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass     11 OBEX
      bInterfaceProtocol      0
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      CDC OBEX:
        bcdVersion           1.00
      CDC Union:
        bMasterInterface        7
        bSlaveInterface         8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        8
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        8
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        9
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      CDC ACM:
        bmCapabilities       0x06
          sends break
          line coding and serial state
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          10
      CDC Union:
        bMasterInterface        9
        bSlaveInterface         10
      UNRECOGNIZED CDC:  04 24 fd 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       10
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       11
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass    254
      bInterfaceProtocol      0
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      UNRECOGNIZED CDC:  05 24 ab 05 5c
      CDC Union:
        bMasterInterface        11
        bSlaveInterface         12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       12
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       12
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       13
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass    253
      bInterfaceProtocol      0
      iInterface              0
      CDC Header:
        bcdCDC               1.10
      UNRECOGNIZED CDC:  05 24 fc 00 01
      CDC Union:
        bMasterInterface        13
        bSlaveInterface         14
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       14
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       14
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      ** UNRECOGNIZED:  04 24 fd 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x09  EP 9 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

dmesg | tail shows:
[FONT=Times New Roman][SIZE=3][89625.076850] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89625.079834] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89625.093851] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 10 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89625.096836] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89625.099833] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89652.462766] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89652.465746] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89652.474761] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 10 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89652.477753] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -62[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][89652.480760] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -62[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]tailf /var/log/messages shows:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 12:32:51 ainl6m001 kernel: [86863.059653] usb 1-3: bad CDC descriptors[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 12:32:51 ainl6m001 kernel: [86863.059670] usb 1-3: bad CDC descriptors[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 12:45:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 13:05:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 13:25:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 13:45:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 14:05:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 14:25:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 14:45:17 ainl6m001 -- MARK --[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sep 23 15:05:17 ainl6m001 -- MARK –[/SIZE][/FONT]

Does anyone have an idea?

---

