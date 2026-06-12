---
title: "installing drivers for a USB device"
date: 2010-06-23
forum: Hardware
---

### Post by manikantan_nambi on 2010-06-23
Hi, 
I have USB device for which I am trying to install drivers and write a custom software to use it. 

I have done it in windows but am planning to shift to Linux. 
The way it works in windows is that the drivers for the device install a virtual serial port driver so that the device connected to the USB port acts as a serial device. I have written code to do serial communication with the virtual serial port and control the device. 

In linux I don't have drivers for the device. 
lsusb shows the following for the device
```

$ sudo lsusb -v -d 0403:ea74

Bus 004 Device 003: ID 0403:ea74 Future Technology Devices International, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xea74 
  bcdDevice            6.00
  iManufacturer           1 FTDI
  iProduct                2 NanoControl 4
  iSerial                 3 NCS7WXED
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 NanoControl 4
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


```

This means the device is being recognized ? Now how do I install drivers for the device and be able to use it as a serial device ?

Thank You 
Manikantan
(manikantan_nambi@yahoo.com)

---

### Post by manikantan_nambi on 2010-06-24
help plz !!!!

---

