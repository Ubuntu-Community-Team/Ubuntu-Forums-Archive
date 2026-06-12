---
title: "Lirc and Northstar Systems MCEusb2"
date: 2008-10-15
forum: Hardware
---

### Post by Nerachnaku on 2008-10-15
Hello, I've been all over trying to get the ir receiver that came with my HP9250f. I have determined (by booting into windows) that it is a standard MCE remote with exception to it's device ID. Knowing this I patched the mceusb2.c file in the Lirc source code with the proper device ID listed in the output below. Still whenever when I start Lirc no devices are created and/or recognized as a receiver. If anyone has any ideas or has had this problem any help would be apreciated. Thanks.

Below are the relevant lsusb and cat /proc/bus/usb/devices output if you want anything else I will be glad to post it.

```
Bus 008 Device 035: ID 04eb:e004 Northstar Systems, Inc. 

```

```
T:  Bus=08 Lev=02 Prnt=33 Port=01 Cnt=02 Dev#= 35 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04eb ProdID=e004 Rev= 3.60
S:  Manufacturer=028797697842030370
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=A00000001
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  32 Ivl=8ms
E:  Ad=82(I) Atr=03(Int.) MxPS=  32 Ivl=8ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=8ms

```

---

### Post by jherm on 2009-03-10
It appears we have the same IR transceiver and I'm looking to make mine work. Did you ever make any progress on this?

More information:

```
[jherm@desktop Desktop]$ sudo lsusb -vd 04eb:e004

Bus 002 Device 005: ID 04eb:e004 Northstar Systems, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04eb Northstar Systems, Inc.
  idProduct          0xe004 
  bcdDevice            3.60
  iManufacturer           1 028797697842030370
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 A00000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           57
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               8
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      28
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)
```

---

