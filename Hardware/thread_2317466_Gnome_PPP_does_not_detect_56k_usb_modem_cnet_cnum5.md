---
title: "Gnome PPP does not detect 56k usb modem cnet cnum56-rs in ubuntu 14.04"
date: 2016-03-16
forum: Hardware
---

### Post by Jesus_R_C on 2016-03-16
I have Ubuntu 14.04 LTS (64 bits) and try to run a 56k modem usb cnet, modem data are as follows:

Brand: CNet

Model: CNUM56-RS

Chipset: Conexant

When I run `lsusb` with the connected modem out the following:
    
```
    $ lsusb
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 007: ID 0572:1300 Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
    Bus 004 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

This is the modem:

> Bus 005 Device 007: ID 0572:1300 Conexant Systems (Rockwell), Inc.

> SoftK56 Data Fax Voice CARP


The more detailed output is:

```
    $ lsusb -v -d 0572:1300
    
    Bus 005 Device 007: ID 0572:1300 Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP
    Device Descriptor:
      bLength                18
      bDescriptorType         1
      bcdUSB               1.10
      bDeviceClass            2 Communications
      bDeviceSubClass         0 
      bDeviceProtocol       255 
      bMaxPacketSize0        64
      idVendor           0x0572 Conexant Systems (Rockwell), Inc.
      idProduct          0x1300 SoftK56 Data Fax Voice CARP
      bcdDevice            1.00
      iManufacturer           1 (error)
      iProduct                2 (error)
      iSerial                 0 
      bNumConfigurations      1
      Configuration Descriptor:
        bLength                 9
        bDescriptorType         2
        wTotalLength           73
        bNumInterfaces          2
        bConfigurationValue     1
        iConfiguration          3 (error)
        bmAttributes         0xa0
          (Bus Powered)
          Remote Wakeup
        MaxPower              260mA
        Interface Descriptor:
          bLength                 9
          bDescriptorType         4
          bInterfaceNumber        0
          bAlternateSetting       0
          bNumEndpoints           2
          bInterfaceClass        10 CDC Data
          bInterfaceSubClass      0 Unused
          bInterfaceProtocol      0 
          iInterface              4 (error)
          Endpoint Descriptor:
            bLength                 7
            bDescriptorType         5
            bEndpointAddress     0x01  EP 1 OUT
            bmAttributes            2
              Transfer Type            Bulk
              Synch Type               None
              Usage Type               Data
            wMaxPacketSize     0x0040  1x 64 bytes
            bInterval               0
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
        Interface Descriptor:
          bLength                 9
          bDescriptorType         4
          bInterfaceNumber        1
          bAlternateSetting       0
          bNumEndpoints           1
          bInterfaceClass         2 Communications
          bInterfaceSubClass      1 Direct Line
          bInterfaceProtocol    255 
          iInterface              4 (error)
          Endpoint Descriptor:
            bLength                 7
            bDescriptorType         5
            bEndpointAddress     0x82  EP 2 IN
            bmAttributes            3
              Transfer Type            Interrupt
              Synch Type               None
              Usage Type               Data
            wMaxPacketSize     0x0040  1x 64 bytes
            bInterval               1
          CDC Header:
            bcdCDC               1.10
          CDC Union:
            bMasterInterface        0
            bSlaveInterface         1 
          CDC Call Management:
            bmCapabilities       0x00
            bDataInterface          1
          UNRECOGNIZED CDC:  04 24 03 00
          Country Selection:
            iCountryCodeRelDate        5 (error)
            wCountryCode          0x4803
    Device Status:     0x0001
      Self Powered
```

The `tty` I have are (I do not have `/dev/modem`):

```
    $ ls -l /dev/tty*
    crw-rw-rw- 1 root tty     5,  0 mar 15 19:03 /dev/tty
    crw--w---- 1 root tty     4,  0 mar 15 15:29 /dev/tty0
    crw-rw---- 1 root tty     4,  1 mar 15 15:29 /dev/tty1
    crw--w---- 1 root tty     4, 10 mar 15 15:29 /dev/tty10
    crw--w---- 1 root tty     4, 11 mar 15 15:29 /dev/tty11
    crw--w---- 1 root tty     4, 12 mar 15 15:29 /dev/tty12
    crw--w---- 1 root tty     4, 13 mar 15 15:29 /dev/tty13
    crw--w---- 1 root tty     4, 14 mar 15 15:29 /dev/tty14
    crw--w---- 1 root tty     4, 15 mar 15 15:29 /dev/tty15
    crw--w---- 1 root tty     4, 16 mar 15 15:29 /dev/tty16
    crw--w---- 1 root tty     4, 17 mar 15 15:29 /dev/tty17
    crw--w---- 1 root tty     4, 18 mar 15 15:29 /dev/tty18
    crw--w---- 1 root tty     4, 19 mar 15 15:29 /dev/tty19
    crw-rw---- 1 root tty     4,  2 mar 15 15:29 /dev/tty2
    crw--w---- 1 root tty     4, 20 mar 15 15:29 /dev/tty20
    crw--w---- 1 root tty     4, 21 mar 15 15:29 /dev/tty21
    crw--w---- 1 root tty     4, 22 mar 15 15:29 /dev/tty22
    crw--w---- 1 root tty     4, 23 mar 15 15:29 /dev/tty23
    crw--w---- 1 root tty     4, 24 mar 15 15:29 /dev/tty24
    crw--w---- 1 root tty     4, 25 mar 15 15:29 /dev/tty25
    crw--w---- 1 root tty     4, 26 mar 15 15:29 /dev/tty26
    crw--w---- 1 root tty     4, 27 mar 15 15:29 /dev/tty27
    crw--w---- 1 root tty     4, 28 mar 15 15:29 /dev/tty28
    crw--w---- 1 root tty     4, 29 mar 15 15:29 /dev/tty29
    crw-rw---- 1 root tty     4,  3 mar 15 15:29 /dev/tty3
    crw--w---- 1 root tty     4, 30 mar 15 15:29 /dev/tty30
    crw--w---- 1 root tty     4, 31 mar 15 15:29 /dev/tty31
    crw--w---- 1 root tty     4, 32 mar 15 15:29 /dev/tty32
    crw--w---- 1 root tty     4, 33 mar 15 15:29 /dev/tty33
    crw--w---- 1 root tty     4, 34 mar 15 15:29 /dev/tty34
    crw--w---- 1 root tty     4, 35 mar 15 15:29 /dev/tty35
    crw--w---- 1 root tty     4, 36 mar 15 15:29 /dev/tty36
    crw--w---- 1 root tty     4, 37 mar 15 15:29 /dev/tty37
    crw--w---- 1 root tty     4, 38 mar 15 15:29 /dev/tty38
    crw--w---- 1 root tty     4, 39 mar 15 15:29 /dev/tty39
    crw-rw---- 1 root tty     4,  4 mar 15 15:29 /dev/tty4
    crw--w---- 1 root tty     4, 40 mar 15 15:29 /dev/tty40
    crw--w---- 1 root tty     4, 41 mar 15 15:29 /dev/tty41
    crw--w---- 1 root tty     4, 42 mar 15 15:29 /dev/tty42
    crw--w---- 1 root tty     4, 43 mar 15 15:29 /dev/tty43
    crw--w---- 1 root tty     4, 44 mar 15 15:29 /dev/tty44
    crw--w---- 1 root tty     4, 45 mar 15 15:29 /dev/tty45
    crw--w---- 1 root tty     4, 46 mar 15 15:29 /dev/tty46
    crw--w---- 1 root tty     4, 47 mar 15 15:29 /dev/tty47
    crw--w---- 1 root tty     4, 48 mar 15 15:29 /dev/tty48
    crw--w---- 1 root tty     4, 49 mar 15 15:29 /dev/tty49
    crw-rw---- 1 root tty     4,  5 mar 15 15:29 /dev/tty5
    crw--w---- 1 root tty     4, 50 mar 15 15:29 /dev/tty50
    crw--w---- 1 root tty     4, 51 mar 15 15:29 /dev/tty51
    crw--w---- 1 root tty     4, 52 mar 15 15:29 /dev/tty52
    crw--w---- 1 root tty     4, 53 mar 15 15:29 /dev/tty53
    crw--w---- 1 root tty     4, 54 mar 15 15:29 /dev/tty54
    crw--w---- 1 root tty     4, 55 mar 15 15:29 /dev/tty55
    crw--w---- 1 root tty     4, 56 mar 15 15:29 /dev/tty56
    crw--w---- 1 root tty     4, 57 mar 15 15:29 /dev/tty57
    crw--w---- 1 root tty     4, 58 mar 15 15:29 /dev/tty58
    crw--w---- 1 root tty     4, 59 mar 15 15:29 /dev/tty59
    crw-rw---- 1 root tty     4,  6 mar 15 15:29 /dev/tty6
    crw--w---- 1 root tty     4, 60 mar 15 15:29 /dev/tty60
    crw--w---- 1 root tty     4, 61 mar 15 15:29 /dev/tty61
    crw--w---- 1 root tty     4, 62 mar 15 15:29 /dev/tty62
    crw--w---- 1 root tty     4, 63 mar 15 15:29 /dev/tty63
    crw--w---- 1 root tty     4,  7 mar 15 15:29 /dev/tty7
    crw--w---- 1 root tty     4,  8 mar 15 15:29 /dev/tty8
    crw--w---- 1 root tty     4,  9 mar 15 15:29 /dev/tty9
    crw------- 1 root root    5,  3 mar 15 15:29 /dev/ttyprintk
    crw-rw---- 1 root dialout 4, 64 mar 15 15:49 /dev/ttyS0
    crw-rw---- 1 root dialout 4, 65 mar 15 15:29 /dev/ttyS1
    crw-rw---- 1 root dialout 4, 74 mar 15 15:29 /dev/ttyS10
    crw-rw---- 1 root dialout 4, 75 mar 15 15:29 /dev/ttyS11
    crw-rw---- 1 root dialout 4, 76 mar 15 15:29 /dev/ttyS12
    crw-rw---- 1 root dialout 4, 77 mar 15 15:29 /dev/ttyS13
    crw-rw---- 1 root dialout 4, 78 mar 15 15:29 /dev/ttyS14
    crw-rw---- 1 root dialout 4, 79 mar 15 15:29 /dev/ttyS15
    crw-rw---- 1 root dialout 4, 80 mar 15 15:29 /dev/ttyS16
    crw-rw---- 1 root dialout 4, 81 mar 15 15:29 /dev/ttyS17
    crw-rw---- 1 root dialout 4, 82 mar 15 15:29 /dev/ttyS18
    crw-rw---- 1 root dialout 4, 83 mar 15 15:29 /dev/ttyS19
    crw-rw---- 1 root dialout 4, 66 mar 15 15:29 /dev/ttyS2
    crw-rw---- 1 root dialout 4, 84 mar 15 15:29 /dev/ttyS20
    crw-rw---- 1 root dialout 4, 85 mar 15 15:29 /dev/ttyS21
    crw-rw---- 1 root dialout 4, 86 mar 15 15:29 /dev/ttyS22
    crw-rw---- 1 root dialout 4, 87 mar 15 15:29 /dev/ttyS23
    crw-rw---- 1 root dialout 4, 88 mar 15 15:29 /dev/ttyS24
    crw-rw---- 1 root dialout 4, 89 mar 15 15:29 /dev/ttyS25
    crw-rw---- 1 root dialout 4, 90 mar 15 15:29 /dev/ttyS26
    crw-rw---- 1 root dialout 4, 91 mar 15 15:29 /dev/ttyS27
    crw-rw---- 1 root dialout 4, 92 mar 15 15:29 /dev/ttyS28
    crw-rw---- 1 root dialout 4, 93 mar 15 15:29 /dev/ttyS29
    crw-rw---- 1 root dialout 4, 67 mar 15 15:29 /dev/ttyS3
    crw-rw---- 1 root dialout 4, 94 mar 15 15:29 /dev/ttyS30
    crw-rw---- 1 root dialout 4, 95 mar 15 15:29 /dev/ttyS31
    crw-rw---- 1 root dialout 4, 68 mar 15 15:29 /dev/ttyS4
    crw-rw---- 1 root dialout 4, 69 mar 15 15:29 /dev/ttyS5
    crw-rw---- 1 root dialout 4, 70 mar 15 15:29 /dev/ttyS6
    crw-rw---- 1 root dialout 4, 71 mar 15 15:29 /dev/ttyS7
    crw-rw---- 1 root dialout 4, 72 mar 15 15:29 /dev/ttyS8
    crw-rw---- 1 root dialout 4, 73 mar 15 15:29 /dev/ttyS9
```

When I remove and then plug the modem back in, the `dmesg` is:

```
    $ dmesg | tail
    [15733.067656] usb 5-1: USB disconnect, device number 7
    [15739.766856] usb 5-1: new full-speed USB device number 8 using ohci-pci
    [15739.933825] usb 5-1: New USB device found, idVendor=0572, idProduct=1300
    [15739.933844] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [15739.933854] usb 5-1: Product: USB HSF Modem
    [15739.933863] usb 5-1: Manufacturer: Conexant Systems, Inc.
```

But when I tell Gnome PPP, it says "No modem was found in the system."

I want to use to send and receive faxes using efax-gtk, which settings am I missing?

Thanks in advance for your answers.

---

