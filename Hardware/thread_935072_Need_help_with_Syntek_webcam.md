---
title: "Need help with Syntek webcam"
date: 2008-10-01
forum: Hardware
---

### Post by davbren on 2008-10-01
Hi, I've been investigating how to install the syntek webcam on linux and I can't work out how. I keep getting an "Error 2" message. Is anyone else getting this?

When I type in lsusb into the terminal I get the message.

```
Bus 004 Device 002: ID 174f:5931 Syntek 
```

When I run cheese, I see no picture but in the preferences box there is 

```
USB 2.0 UVC PC Camera (/dev/video0) 
```

---

### Post by airtonix on 2008-10-01
just so others who come here who may be able to help, lets get more info : 

1 - provide details on how you tried to connect, ie where did your error msg result from?
2 - provide output from : ```
lsusb -s 004:002 -vvv
```
3 - a link to the manufacturers website for product, specifically a page that would detail the chipset numbers.

---

### Post by davbren on 2008-10-01
hey, thx for your quick response. 

```

Bus 004 Device 002: ID 174f:5931 Syntek 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0x5931 
  bcdDevice           11.20
  iManufacturer           2 Syntek
  iProduct                3 USB2.0 UVC PC Camera
  iSerial                 4 0001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          519
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
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           51
        dwClockFrequency        3.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00000000
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000013f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          Backlight Compensation
        iProcessing             0 
        bmVideoStandards     0x 0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               6
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
        bNumFormats                        1
        wTotalLength                      341
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       4
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       1
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors               10
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
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
        dwMinBitRate                 18432000
        dwMaxBitRate                 18432000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         500000
        bFrameIntervalType                  1
        dwFrameInterval( 0)            500000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  1152000
        dwMaxBitRate                  1152000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         416666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            416666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  1520640
        dwMaxBitRate                  1520640
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         416666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            416666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                  4608000
        dwMaxBitRate                  4608000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         416666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            416666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                  6082560
        dwMaxBitRate                  6082560
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         416666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            416666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            800
        wHeight                           600
        dwMinBitRate                  8640000
        dwMaxBitRate                  8640000
        dwMaxVideoFrameBufferSize      960000
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1024
        wHeight                           768
        dwMinBitRate                 14155776
        dwMaxBitRate                 14155776
        dwMaxVideoFrameBufferSize     1572864
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                 18432000
        dwMaxBitRate                 18432000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         9
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           960
        dwMinBitRate                 22118400
        dwMaxBitRate                 22118400
        dwMaxVideoFrameBufferSize     2457600
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                        10
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                 23592960
        dwMaxBitRate                 23592960
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            10
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               1
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        bNumCompressionPatterns             1
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     0 (Unspecified)
        bTransferCharacteristics            0 (Unspecified)
        bMatrixCoefficients                 0 (Unspecified)
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
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



```


This is the output from that code you gave me. 

I got the error 2 message from the syntek webcam driver compilation.

Its an inbuilt webcam on a Samsung Q310 machine.

This is the site I used for my compilation instructions. 

[http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html]("http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html")

---

### Post by davbren on 2008-10-03
I tried runnign amsn and configuring the webcam. It seems to see the webcam but I can't see any picture there. Its just a black screen... any ideas? One of the reasons I bought the laptop was for the webcam lol.

---

### Post by sukhhari on 2008-10-03
Try to Install Cheese from your Synaptic Update Manager.

:guitar:

---

### Post by davbren on 2008-10-04
I have cheese installed and it says there is a webcam but doesn't show a picture.

---

### Post by ideefixe on 2008-10-15
Have you tested the webcam with luvcview (it's in the universe repo)?

This might be also helpful:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-October/004095.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-October/004095.html)
(You will need the fresh version of uvcvideo driver, probably from svn.)

With this option (quirks=16) the webcam on my q310 works in skype and luvcview.

---

### Post by davbren on 2008-10-15
Hi cheers, for your help. It appears that I already have the latest driver, but I'm getting a black screen when running luvcview... any ideas?

Does you cam work in cheese?

---

### Post by ideefixe on 2008-10-15
No, it does not work in cheese, but works in other programs.

The really important thing is to load the driver with "quirks=16" option:
Try unloading the module first: rmmod uvcvideo
Then load with this option: modprobe uvcvideo quirks=16

---

### Post by davbren on 2008-10-22
Hey, That got it working. The problem now is that it seems to "lose" to driver with the "quirks" bit after each boot... Any ideas?

---

### Post by ideefixe on 2008-10-23
To change the module options during autoload simply edit /etc/modprobe.d/options - add "options uvcvideo quirks=16"

BTW, the camera was added to the developper's database, so you can also check the latest svn, no more "quirks" is required with it.

---

### Post by davbren on 2008-10-24
will it work on cheese? Currently its really temperamental. I've taken a few pictures with it but at the moment its just showing the test card. luvcview works well as does vlc...

---

### Post by ideefixe on 2008-10-24
It's working quite strange with cheese for me - most often cheese is unable to get the picture from camera, sometimes it just hangs and very rarely I'm able to take pictures and videos :(

By the way, luvcview is also able to take pictures.

The camera works reliably with skype.

---

### Post by davbren on 2008-10-24
It also works (if a little slowly) on aMSN. i've managed to take screenies with vlc and luvcview. Was really lookin for the fun factor of cheese tho. I'm really lookin to advertise linux to people who aern't really bothered with what they use and are open minded. They need to see cool fun stuff.

---

### Post by tcwden on 2009-01-16
Does the "quirks" option supported by ubuntu 8.04? I've got the following message when I try to use the quirks option:

dennis@dennis-desktop:~$ sudo rmmod uvcvideo
dennis@dennis-desktop:~$ sudo modprobe uvcvideo quirks=16
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-23-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dennis@dennis-desktop:~$ dmesg | grep uvcvideo
[86524.218907] usbcore: registered new interface driver uvcvideo
[86550.490581] usbcore: deregistering interface driver uvcvideo
[86569.773037] uvcvideo: Unknown parameter `quirks'

Dennis

---

### Post by davbren on 2009-02-08
Ok I've installed the driver and for some reason the webcam doesn't work, sometimes I'll get a still but no video...

---

