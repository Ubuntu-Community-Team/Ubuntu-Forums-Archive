---
title: "How to find HID Device Descriptor on 9.10"
date: 2009-11-01
forum: Hardware
---

### Post by sparker256 on 2009-11-01
Under 9.04 the following commands work fine but not under 9.10. Is there any good reason or a new command.

This is from 9.04
```

[  168.181940] input: Saitek Pro Flight Multi Panel as /devices/pci0000:00/0000:00:0a.0/usb2/2-5/2-5:1.0/input/input8
[  168.184772] generic-usb 0003:06A3:0D06.0003: input,hidraw1: USB HID v1.00 Device [Saitek Pro Flight Multi Panel] on usb-0000:00:0a.0-5/input0
root@bill-desktop:/sys/bus/usb/drivers/usbhid# sudo echo -n 2-5:1.0 >unbind
root@bill-desktop:/sys/bus/usb/drivers/usbhid# lsusb -d 06a3:0d06 -vvv

Bus 002 Device 005: ID 06a3:0d06 Saitek PLC 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x06a3 Saitek PLC
  idProduct          0x0d06 
  bcdDevice            1.40
  iManufacturer           1 Saitek
  iProduct                2 Pro Flight Multi Panel
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              150mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      76
           Report Descriptor: (length is 76)
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Usage Page, data= [ 0x09 ] 9
                            Buttons
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            Button 1 (Primary)
            Item(Local ): Usage Maximum, data= [ 0x14 ] 20
                            (null)
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x14 ] 20
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x04 ] 4
            Item(Main  ): Input, data= [ 0x01 ] 1
                            Constant Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            Pointer
            Item(Local ): Usage Maximum, data= [ 0x0a ] 10
                            (null)
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x0a ] 10
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x08 ] 8
                            LEDs
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            NumLock
            Item(Local ): Usage Maximum, data= [ 0x08 ] 8
                            Do not disturb
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x08 ] 8
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x09 ] 9
                            Buttons
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            Button 1 (Primary)
            Item(Local ): Usage Maximum, data= [ 0x05 ] 5
                            Button 5
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x05 ] 5
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x03 ] 3
            Item(Main  ): Feature, data= [ 0x03 ] 3
                            Constant Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7



```


Now this is from 9.10

```


[  317.769378] input: Saitek Pro Flight Multi Panel as /devices/pci0000:00/0000:00:0a.0/usb2/2-5/2-5:1.0/input/input8
[  317.769429] generic-usb 0003:06A3:0D06.0003: input,hidraw1: USB HID v1.00 Device [Saitek Pro Flight Multi Panel] on usb-0000:00:0a.0-5/input0
root@bill-910:/sys/bus/usb/drivers/usbhid# echo -n 2-5:1.0 >unbind
root@bill-910:/sys/bus/usb/drivers/usbhid# lsusb -d 06a3:0d06 -vvv

Bus 002 Device 005: ID 06a3:0d06 Saitek PLC 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x06a3 Saitek PLC
  idProduct          0x0d06 
  bcdDevice            1.40
  iManufacturer           1 Saitek
  iProduct                2 Pro Flight Multi Panel
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              150mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 4c 00
      Endpoint Descriptor:
        bLength                 7

```

I want to get rid of 9.04 but until this is resolved I can't.

Thanks Bill

---

