---
title: "HID Keyboard Device not accepting input"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by Directrix1 on 2006-02-27
Well, I have a barcode reader (ZBA ZB-8110) that (without drivers) is recognized as a HID keyboard device in Windows 2000.  In my Ubuntu box however it doesn't scan anything (it is powered though).  Here are the relevant outputs from 'dmesg' and 'lsusb -v'.  From the outputs it looks like it is recognized as a standard HID Keyboard, but it doesn't work at all.  Please help me.
dmesg:
```
[4294694.917000] usb 2-2.2: new low speed USB device using uhci_hcd and address 3
[4294696.580000] usbcore: registered new driver hiddev
[4294696.591000] usbhid: probe of 2-2.2:1.0 failed with error -5
[4294696.591000] usbcore: registered new driver usbhid
[4294696.591000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver

```
lsusb -v:
```
Bus 002 Device 003: ID 04b4:de61 Cypress Semiconductor Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0xde61
  bcdDevice            2.50
  iManufacturer           1 Guest
  iProduct                2 Generic KB-HID
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HID KB
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              5 EP1
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      64
          Report Descriptor: (length is 64)
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x06 ] 6
                            Keyboard
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Usage Page, data= [ 0x07 ] 7
                            Keyboard
            Item(Local ): Usage Maximum, data= [ 0xe7 ] 231
                            GUI Right
            Item(Local ): Usage Minimum, data= [ 0xe0 ] 224
                            Control Left
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x08 ] 8
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Main  ): Input, data= [ 0x01 ] 1
                            Constant Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x05 ] 5
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Usage Page, data= [ 0x08 ] 8
                            LEDs
            Item(Local ): Usage Maximum, data= [ 0x05 ] 5
                            Kana
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            NumLock
            Item(Main  ): Output, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x03 ] 3
            Item(Main  ): Output, data= [ 0x01 ] 1
                            Constant Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x06 ] 6
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Logical Maximum, data= [ 0xe7 0x00 ] 231
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Usage Page, data= [ 0x07 ] 7
                            Keyboard
            Item(Local ): Usage Maximum, data= [ 0xe7 ] 231
                            GUI Right
            Item(Local ): Usage Minimum, data= [ 0x00 ] 0
                            No Event
            Item(Main  ): Input, data= [ 0x00 ] 0
                            Data Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
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

```

---

### Post by Directrix1 on 2006-02-27
Just thought I'd let everyone know.  I got it to work by running 'modprobe usbkbd'.  Works like a charm now.

---

### Post by techiepatrol on 2007-12-06
Dude, great post.  That modprobe command  totally worked for me using the USB Unitech barcode scanner.

Now I have a list of standard commands I type when imaging systems that I converted to barcode font and laminated.  This really expedites my day work.  Thanks a bunch!

---

