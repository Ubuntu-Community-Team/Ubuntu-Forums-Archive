---
title: "LG Electronics Scanworks 600U Scanner"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by Malac on 2006-07-18
This scanner is in device manager but with xsane it is not being detected.
Could any one help.
I have included a section of the output of lsusb -vv in case this is any help.
```

Bus 004 Device 003: ID 0461:0364 Primax Electronics, Ltd LG Electronics Scanwork s 600U Scanner
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0461 Primax Electronics, Ltd
  idProduct          0x0364 LG Electronics Scanworks 600U Scanner
  bcdDevice            0.02
  iManufacturer           2 Primax
  iProduct                1 USB Scanner
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower               48mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        16
      bInterfaceSubClass      1
      bInterfaceProtocol      0
      iInterface              0
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

Thanks in advance.

---

### Post by zxee on 2006-07-19
Have you tried [http://www.sane-project.org/](http://www.sane-project.org/) and checked the supported devices link? I checked there and found that the model you listed is only supported with the 2.4 kernel and the support level listed is "basic". 
[http://www.sane-project.org/cgi-bin/driver.pl?manu=LG&model=600u&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=LG&model=600u&bus=any&v=&p=)

---

### Post by Malac on 2006-07-20
Thanks for the info. Having checked the page I wouldn't know where to start with this though I don't mind kernel compilation if needs be but I was hoping for a 2.6...... solution.
Oh well, Many Thanks.

---

### Post by zxee on 2006-07-20
I would recommend that you add your email to the specific sane backend list, and/or just check that list once in awhile. The drivers do get upgraded and the sane backend developers will respond to users (in my experiance).

---

