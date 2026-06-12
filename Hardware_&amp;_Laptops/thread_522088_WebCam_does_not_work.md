---
title: "WebCam does not work"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by dorakay on 2007-08-10
Hello, I'm just switch myself to Ubuntu in last few months.

Now, I try to use my buildin Web Camera on my laptop
but it's not work. I remember that last time I use Windows XP
I have disable WebCam hardware, so is that cause of this problem.

I try to use Camorama Webcam Viewer but it shows me message
"Could not connect to video device (/dev/video0). Please check conection."


How can I enable my webcam if in that case or any ideas how can i solve
this problem ?

---

### Post by drpaul on 2007-08-10
Built in Webcams can be tricky. Suggest you search the forum for your type of hardware.

Paul

---

### Post by dorakay on 2007-08-13
Thank you for your reply. :)
I'm still search for more information.

command lsusb return result with camera name in it.
so it seems like Ubuntu see the device but does not mount it.
but that's just my guess.

My webcam still doesn't work.

Do anyone have some suggestions ?

---

### Post by Teamgeist on 2007-08-13
Posting the output of lsusb and letting people know what kind of webcam you have might help, I think. ;)

---

### Post by buntunub on 2007-08-13
Post output of lsusb and lsusb -v appended for you webcam. In general, most peoples webcams work out of the box with Ekiga using the built in uvc driver. You can also use luvcview. Check out the linux webcam projects website for a compatibility and driver listing.

---

### Post by dorakay on 2007-08-21
lsusb return this :

> Bus 004 Device 002: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


and lsusb -v show :

> Bus 004 Device 002: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x5603 USB 2.0 Q-tec Webcam 300
  bcdDevice            1.02
  iManufacturer           0 
  iProduct                1 ALI M5603C
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          101
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
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

---

### Post by dorakay on 2007-08-21
It seems like there is no driver for this one yet.

---

### Post by hamiljf on 2008-02-19
Lack of support for Ali M5603C, BisonCam NB Pro device id 0402:5602 was noted in [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61669](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61669) and support was said to be planned for feisty fawn.  I'm on gutsy gibbon and it isn't here... as far as i can tell

---

