---
title: "Kingston datatraveler 2GB memory stick and SD card reader problem"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by esventat on 2008-03-11
Dear all,

I have a USB Kingston 2GB DataTraveler memory stick and card reader that I can not mount on my ubuntu system (it works on windows computers). I search the forums (and found related threads) but I could not find the right answer.

It's an ubuntu 7.10 box (with the default kernel 2.6.22-14 ). Also, I have to say that on the same computer I can mount and work with other USB memory sticks...

At the end, I write the output of lsusb and dmesg.

Any help or pointer to some resources will be very welcomed!

thanks!

--------------------------------------------------------------------

before plug datatraveler

```
# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:8105 Dell Computer Corp. 
Bus 001 Device 007: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 006: ID 046d:08d7 Logitech, Inc. 
Bus 001 Device 005: ID 05e3:0606 Genesys Logic, Inc. 
Bus 001 Device 003: ID 413c:0058 Dell Computer Corp. 
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
```

Then, I clean the dmesg "buffer" (dmesg -c) and I plug the datatraveler 

```
# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 031: ID 0951:1606 Kingston Technology 
Bus 001 Device 030: ID 0951:0169 Kingston Technology 
Bus 001 Device 004: ID 413c:8105 Dell Computer Corp. 
Bus 001 Device 007: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 006: ID 046d:08d7 Logitech, Inc. 
Bus 001 Device 005: ID 05e3:0606 Genesys Logic, Inc. 
Bus 001 Device 003: ID 413c:0058 Dell Computer Corp. 
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

```

(new devices 30 and 31 appeared):

```
# lsusb -vs 31

Bus 001 Device 031: ID 0951:1606 Kingston Technology 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0951 Kingston Technology
  idProduct          0x1606 
  bcdDevice            1.00
  iManufacturer           1 Kingston
  iProduct                5 DataTraveler Card Reader
  iSerial                 3 86152bb3a0e25f
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

```
# lsusb -vs 30

Bus 001 Device 030: ID 0951:0169 Kingston Technology 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0951 Kingston Technology
  idProduct          0x0169 
  bcdDevice            1.00
  iManufacturer           1 Kingston
  iProduct                4 Generic USB Hub Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent     49 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0101 power connect
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```


But a lot of errors are reported by dmesg:

```
# dmesg
[10139.552000] usb 1-8.2: new high speed USB device using ehci_hcd and address 30
[10139.644000] usb 1-8.2: configuration #1 chosen from 1 choice
[10139.644000] hub 1-8.2:1.0: USB hub found
[10139.644000] hub 1-8.2:1.0: 2 ports detected
[10139.948000] usb 1-8.2.1: new high speed USB device using ehci_hcd and address 31
[10140.040000] usb 1-8.2.1: configuration #1 chosen from 1 choice
[10140.040000] scsi11 : SCSI emulation for USB Mass Storage devices
[10140.040000] usb-storage: device found at 31
[10140.040000] usb-storage: waiting for device to settle before scanning
[10145.040000] usb-storage: device scan complete
[10145.040000] scsi 11:0:0:0: Direct-Access     Kingston DataTravelerCR   2.01 PQ: 0 ANSI: 2
[10145.044000] sd 11:0:0:0: [sdb] 8257536 512-byte hardware sectors (4228 MB)
[10145.044000] sd 11:0:0:0: [sdb] Write Protect is off
[10145.044000] sd 11:0:0:0: [sdb] Mode Sense: 00 00 00 00
[10145.044000] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[10145.048000] sd 11:0:0:0: [sdb] 8257536 512-byte hardware sectors (4228 MB)
[10145.048000] sd 11:0:0:0: [sdb] Write Protect is off
[10145.048000] sd 11:0:0:0: [sdb] Mode Sense: 00 00 00 00
[10145.048000] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[10145.048000]  sdb: sdb1
[10145.188000] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[10145.188000] sd 11:0:0:0: Attached scsi generic sg2 type 0
[10145.296000] end_request: I/O error, dev sdb, sector 8257408
[10145.296000] printk: 524 messages suppressed.
[10145.296000] Buffer I/O error on device sdb, logical block 1032176
[10145.300000] end_request: I/O error, dev sdb, sector 8257408
[10145.300000] Buffer I/O error on device sdb, logical block 1032176
[10145.304000] end_request: I/O error, dev sdb, sector 8257520
[10145.304000] Buffer I/O error on device sdb, logical block 1032190
[10145.304000] end_request: I/O error, dev sdb, sector 8257520
[10145.304000] Buffer I/O error on device sdb, logical block 1032190
[10145.308000] end_request: I/O error, dev sdb, sector 0
[10145.308000] Buffer I/O error on device sdb, logical block 0
[10145.308000] end_request: I/O error, dev sdb, sector 0
[10145.308000] Buffer I/O error on device sdb, logical block 0
[10145.312000] end_request: I/O error, dev sdb, sector 0
[10145.312000] Buffer I/O error on device sdb, logical block 0
[10145.316000] end_request: I/O error, dev sdb, sector 8257528
[10145.316000] Buffer I/O error on device sdb, logical block 1032191
[10145.316000] end_request: I/O error, dev sdb, sector 8257528
[10145.316000] Buffer I/O error on device sdb, logical block 1032191
[10145.320000] end_request: I/O error, dev sdb, sector 8257528
[10145.320000] Buffer I/O error on device sdb, logical block 1032191
[10145.324000] end_request: I/O error, dev sdb, sector 8257528
[10145.324000] end_request: I/O error, dev sdb, sector 8257528
[10145.328000] end_request: I/O error, dev sdb, sector 8257528
[10145.332000] end_request: I/O error, dev sdb, sector 8257472
[10145.332000] end_request: I/O error, dev sdb, sector 8257520
[10145.336000] end_request: I/O error, dev sdb, sector 8257528
[10145.340000] end_request: I/O error, dev sdb, sector 8257528
[10145.340000] end_request: I/O error, dev sdb, sector 0
[10145.344000] end_request: I/O error, dev sdb, sector 0
[10145.344000] end_request: I/O error, dev sdb, sector 0
[10145.348000] end_request: I/O error, dev sdb, sector 0
[10145.348000] end_request: I/O error, dev sdb, sector 0
[10145.348000] end_request: I/O error, dev sdb, sector 0
[10145.352000] end_request: I/O error, dev sdb, sector 0
[10145.352000] end_request: I/O error, dev sdb, sector 0
[10145.356000] end_request: I/O error, dev sdb, sector 0
[10145.356000] end_request: I/O error, dev sdb, sector 0
[10145.360000] end_request: I/O error, dev sdb, sector 0
[10145.360000] end_request: I/O error, dev sdb, sector 0
[10145.360000] end_request: I/O error, dev sdb, sector 0
[10145.364000] end_request: I/O error, dev sdb, sector 0
[10145.364000] end_request: I/O error, dev sdb, sector 0
[10145.368000] end_request: I/O error, dev sdb, sector 0
[10145.368000] end_request: I/O error, dev sdb, sector 0
[10145.372000] end_request: I/O error, dev sdb, sector 0
[10145.372000] end_request: I/O error, dev sdb, sector 0
[10145.376000] end_request: I/O error, dev sdb, sector 0
[10145.376000] end_request: I/O error, dev sdb, sector 0
[10145.376000] end_request: I/O error, dev sdb, sector 0
[10145.380000] end_request: I/O error, dev sdb, sector 0
[10145.380000] end_request: I/O error, dev sdb, sector 0
[10145.384000] end_request: I/O error, dev sdb, sector 0
[10145.388000] end_request: I/O error, dev sdb, sector 0
[10145.392000] end_request: I/O error, dev sdb, sector 0
[10145.392000] end_request: I/O error, dev sdb, sector 0
[10145.520000] end_request: I/O error, dev sdb, sector 63
[10145.520000] end_request: I/O error, dev sdb, sector 64
[10145.524000] end_request: I/O error, dev sdb, sector 63
[10145.524000] end_request: I/O error, dev sdb, sector 64
[10145.524000] end_request: I/O error, dev sdb, sector 71
[10145.528000] end_request: I/O error, dev sdb, sector 72
[10145.528000] end_request: I/O error, dev sdb, sector 63
[10145.556000] end_request: I/O error, dev sdb, sector 63
[10145.556000] end_request: I/O error, dev sdb, sector 64
[10145.556000] end_request: I/O error, dev sdb, sector 63
[10145.560000] end_request: I/O error, dev sdb, sector 64
[10145.560000] end_request: I/O error, dev sdb, sector 63
[10145.564000] end_request: I/O error, dev sdb, sector 64
[10145.564000] end_request: I/O error, dev sdb, sector 63
[10145.564000] end_request: I/O error, dev sdb, sector 64
[10145.568000] end_request: I/O error, dev sdb, sector 63
[10145.568000] end_request: I/O error, dev sdb, sector 64
[10145.572000] end_request: I/O error, dev sdb, sector 63
[10145.572000] end_request: I/O error, dev sdb, sector 64
[10145.572000] end_request: I/O error, dev sdb, sector 63
[10145.576000] hub 1-8.2:1.0: hub_port_status failed (err = 0)
[10145.576000] end_request: I/O error, dev sdb, sector 64
[10148.652000] usb 1-8.2.1: reset high speed USB device using ehci_hcd and address 31
```

---

### Post by Kivech on 2008-03-11
Interesting post. I seem to have a similar issue (just now noticed while trying to read from a photo camera memory card).

Seems to me that probably some driver is missing. Would be interesting to know how others got theirs to work.

I'll keep an eye on this thread as well, because I never had problems with this before, except with Ubuntu. Running Gutsy 64 here btw.

Kivech

---

### Post by HHelsinger on 2008-03-12
I have the same problem with the same usb stick.

Sounds like this is related to the frequently reported problem (now several years old) with usb sticks not mounting and generating a "device descriptor read/64 error."   
The only fix anyone reports is to disable ehci-hcd with ```
sudo modprobe -r ehci-hcd
```
the problem with that is that it disables usb2.  

In my case neither Kingston nor Sandisk sticks work -- although they all work properly on a different machine.   Worse yet, the problem seems to go deep enough that on this dual-boot machine they work neither under Gutsy, nor under Windows!

---

