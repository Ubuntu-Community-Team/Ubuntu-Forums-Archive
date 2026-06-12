---
title: "Tasco USB Microscope"
date: 2014-06-05
forum: Hardware
---

### Post by bswarm2 on 2014-06-05
I'm trying to get a Tasco 780200T Digital USB Microscope working on 14.04. No luck so far with VLC, Cheese, guvcview, etc. Any help would be appreciated.
lsusb -v results...

Bus 001 Device 004: ID 1871:0516 Aveo Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x1871 Aveo Technology Corp.
  idProduct          0x0516 
  bcdDevice            3.07
  iManufacturer           1 AVEO Technology Corp.
  iProduct                2 USB2.0 Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          411
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass        255 Vendor Specific Class
      bFunctionSubClass       3 
      bFunctionProtocol       0 
      iFunction               2 USB2.0 Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      0 
      iInterface              2 USB2.0 Camera
      ** UNRECOGNIZED:  0d 24 01 00 01 4d 00 80 c3 c9 01 01 01
      ** UNRECOGNIZED:  12 24 02 01 01 02 00 00 00 00 00 00 00 00 03 00 00 00
      ** UNRECOGNIZED:  09 24 03 02 01 01 00 04 00
      ** UNRECOGNIZED:  0b 24 05 03 01 00 00 02 1b 04 00
      ** UNRECOGNIZED:  1a 24 06 04 52 f2 b8 aa d1 8e 72 49 8c ed 96 b1 7f 04 40 8b 01 01 03 01 03 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               7
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         1
        wTotalLength                      207
        bEndPointAddress                  131
        bmInfo                              0
        bTerminalLink                       2
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                5
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 36864000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 48660480
        dwMaxBitRate                 48660480
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         9
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           960
        dwMinBitRate                157286400
        dwMaxBitRate                157286400
        dwMaxVideoFrameBufferSize     2457600
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                        10
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                157286400
        dwMaxBitRate                157286400
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            10
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               1
        wWidth( 0)                        640
        wHeight( 0)                       480
        bNumCompressionPatterns             1
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x020c  1x 524 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x030c  1x 780 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x03fc  1x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0bfc  2x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13fc  3x 1020 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

### Post by bswarm2 on 2014-06-06
I got this working in Virtualbox (WinXP) by following the post here [http://ubuntuforums.org/showthread.php?t=761986&page=2&p=8963427#post8963427](http://ubuntuforums.org/showthread.php?t=761986&page=2&p=8963427#post8963427) to get the USB device recognized, but would still like to get this working natively in Linux.
 I've tried the solution at [http://www.linuxtv.org/](http://www.linuxtv.org/) and Googled "Device ID 1871:0516" but still no luck.
Any ideas?

---

### Post by robert127 on 2014-09-03
I have this same microscope with the same issue. 

Found this...

[http://sourceforge.net/p/linux-uvc/mailman/message/32434617/](http://sourceforge.net/p/linux-uvc/mailman/message/32434617/)

Think it will resolve the issue. However, I'm a total noob and don't know how to apply the patch after editing the file so I don't know if it will work or not.  Anyone that can help me, it would be greatly appreciated.

---

### Post by robert127 on 2014-09-04
So I got it working.  I have no idea if I did it the "RIGHT" way and I don't know if my other web cam will work, but I'm using it in "Cheese" right now.

Here's what I did... If some one wants to refine it so the "RIGHT" instructions are here.  Please do so...

Onward:

```
~ $git clone git://linuxtv.org/media_build.git 
~/media_build $./build --main-git
~/media_build $gedit drivers/media/usb/uvc/uvc_driver.c
```

Look for this section near line #2405

```

    /* Aveo Technology USB 2.0 Camera */
    { .match_flags        = USB_DEVICE_ID_MATCH_DEVICE
                | USB_DEVICE_ID_MATCH_INT_INFO,
      .idVendor        = 0x1871,
      .idProduct        = 0x0306,
      .bInterfaceClass    = USB_CLASS_VIDEO,
      .bInterfaceSubClass    = 1,
      .bInterfaceProtocol    = 0,
      .driver_info        = UVC_QUIRK_PROBE_MINMAX
                | UVC_QUIRK_PROBE_EXTRAFIELDS },
```

And insert immediately after it the following...
```

    /* Aveo Technology USB 2.0 Camera */
    { .match_flags        = USB_DEVICE_ID_MATCH_DEVICE
                | USB_DEVICE_ID_MATCH_INT_INFO,
      .idVendor        = 0x1871,
      .idProduct        = 0x0516,
      .bInterfaceClass    = USB_CLASS_VENDOR_SPEC,
      .bInterfaceSubClass    = 1,
      .bInterfaceProtocol    = 0 },

```
Save
```

~/media_build $apt-get install linux-generic


~/media_build $make -C ../v4l
~/media_build $sudo make -C ../ install
~/media_build $sudo make -C .. rmmod
~/media_build $sudo modprobe uvcvideo

```

[COLOR=#000000][FONT=monospace]And that worked for me.  I probably did it wrong, but I can't argue with the results.[/FONT][/COLOR]

---

### Post by bswarm2 on 2014-09-05
Well done, works great! I had to reboot to get it to show up but all works. Thank you.

---

