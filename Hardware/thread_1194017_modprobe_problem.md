---
title: "modprobe problem"
date: 2009-06-22
forum: Hardware
---

### Post by thirddeep on 2009-06-22
I have recently upgraded to 8.10 (I prefer to stay 1 release behind) and now I see the following in ps -ef :

```
root      7650     1  0 11:15 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
root      7817     1  0 11:18 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
root      7992     1  0 11:21 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
root      8158     1  0 11:24 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
root      8305     1  0 11:27 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
root      8450     1  0 11:30 ?        00:00:00 /sbin/modprobe -Q usb:v046Dp0896d0100dcFFdscFFdpFFicFFisc00ip00
```

The longer the laptop is on, the longer that list get.  lsusb tells me that 046D is : 

```
Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
```

The mouse works without problems.

Here is a lsusb -v output for just that device :

```

Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc501 Cordless Mouse Receiver
  bcdDevice            9.10
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      82
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

Any help to track down this problem would be appreciated !

Thd.

---

### Post by thirddeep on 2009-06-22
I just noticed, that udevd is at 100% CPU all the time.  This does not help :(

---

