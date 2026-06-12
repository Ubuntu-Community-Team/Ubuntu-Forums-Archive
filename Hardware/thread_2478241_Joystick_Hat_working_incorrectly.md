---
title: "Joystick Hat working incorrectly"
date: 2022-08-20
forum: Hardware
---

### Post by byteart-studios on 2022-08-20
I've got a Flashfire Cobra V6 ( [https://flashfire.tw/en/items/8b0eea](https://flashfire.tw/en/items/8b0eea) ) and the hat instead of working as intended it reports as a single axis with each hat direction giving a different value, and axis value stays in that direction until I press a different direction. I've tested it in Windows and it works as intended so a factory defect is ruled out

lsusb -vd 11c0:5606 output:
```

Bus 004 Device 019: ID 11c0:5606 Betop USB JoystickDevice Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x11c0 Betop
  idProduct          0x5606 
  bcdDevice            1.22
  iManufacturer           0 
  iProduct                2 USB Joystick
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0022
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     232
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
        bInterval               1
Device Status:     0x0000
  (Bus Powered)



```

dmesg gives the following when it's connected:
```

[302870.066849] input: USB Joystick as /devices/pci0000:00/0000:00:02.4/0000:01:00.0/usb4/4-2/4-2.4/4-2.4:1.0/0003:11C0:5606.0060/input/input155
[302870.067173] hid-generic 0003:11C0:5606.0060: input,hidraw0: USB HID v1.00 Joystick [USB Joystick] on usb-0000:01:00.0-2.4/input0

```

---

