---
title: "Keyboard works with BIOS but not OS"
date: 2017-03-16
forum: Hardware
---

### Post by mike-g2 on 2017-03-16
I'm running Ubuntu-Mate 16.04 on a Lenovo ThinkStation P510.

 My keyboard and mouse used to work, but I installed a second nvidia video card and reset the bios settings.  The keyboard and mouse work in BIOS set up but not when the OS is booted and at the lightdm login screen.  If I do an lsusb, the keyboard and mouse are visible to the OS, but I can't decipher anything else from the output (below).

```

Bus 003 Device 009: ID 047d:1020 Kensington Expert Mouse Trackball
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x047d Kensington
  idProduct          0x1020 Expert Mouse Trackball
  bcdDevice            1.00
  iManufacturer           1 Kensington     
  iProduct                2 Kensington Expert Mouse
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
    MaxPower              100mA
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
          wDescriptorLength      52
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


```


I'm wondering what steps I can take next to diagnose and fix this problem.

---

### Post by mike-g2 on 2017-03-16
Just solved the problem by
```

 sudo apt-get install xserver-xorg-input-all

```
I am guessing I removed these when trying to reset the X server.

---

