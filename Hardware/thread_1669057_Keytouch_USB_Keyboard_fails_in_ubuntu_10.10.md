---
title: "Keytouch USB Keyboard fails in ubuntu 10.10"
date: 2011-01-17
forum: Hardware
---

### Post by kholis on 2011-01-17
I have Keytouch IEC 60945 [http://www.keytouch.no/default.asp?page=84]("http://www.keytouch.no/default.asp?page=84") keyboard that i need to use in linux environment. But its failed to detect properly in ubuntu 10.10

In windows it's works without installing any driver. plug and play just like common usb keyboard.

```
$ tail -f /var/log/syslog

Jan 17 17:56:40 kalau kernel: [  101.154249] usb 2-1.1: new high speed USB device using ehci_hcd and address 8
Jan 17 17:56:40 kalau kernel: [  101.246686] hub 2-1.1:1.0: USB hub found
Jan 17 17:56:40 kalau kernel: [  101.246886] hub 2-1.1:1.0: 4 ports detected
Jan 17 17:56:40 kalau kernel: [  101.517827] usb 2-1.1.4: new full speed USB device using ehci_hcd and address 9
Jan 17 17:56:45 kalau kernel: [  106.608775] generic-usb: probe of 0003:0926:3333.0003 failed with error -32
```

```
kholis@kalau:~$ lsusb 

Bus 002 Device 011: ID 0926:3333  
Bus 002 Device 010: ID 04cc:1521 ST-Ericsson USB 2.0 Hub
Bus 002 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 004: ID 04f2:b1c1 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

kholis@kalau:~$ sudo lsusb -vvv -d 0926:3333

Bus 002 Device 011: ID 0926:3333  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0926 
  idProduct          0x3333 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          3 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              250mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              4 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     103
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
cannot read device status, Broken pipe (32)

kholis@kalau:~$ sudo lsusb -vvv -d 04cc:1521

Bus 002 Device 010: ID 04cc:1521 ST-Ericsson USB 2.0 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x04cc ST-Ericsson
  idProduct          0x1521 USB 2.0 Hub
  bcdDevice            2.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x00b2
    No power switching (usb 1.0)
    No overcurrent protection
    TT think time 16 FS bits
    Port indicators
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0103 power enable connect
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

need suggestion. thanks

---

### Post by kholis on 2011-02-22
Solved. Please see the following thread [http://marc.info/?t=129610043500002&r=1&w=2](http://marc.info/?t=129610043500002&r=1&w=2)

---

