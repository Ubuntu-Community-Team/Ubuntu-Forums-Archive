---
title: "Aveo USB camera dont work."
date: 2017-04-01
forum: Hardware
---

### Post by Portaro on 2017-04-01
There are any firmware or software to make tis camera work ,   I'm on Lubuntu 14.04 with kernel - 
3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux .

ID 1871:01f0 Aveo Technology Corp.

Here I put the message of lsusb -D command  &#8594;




```
$ lsusb -D /dev/bus/usb/003/005
            Device: ID 1871:01f0 Aveo Technology Corp.
            Couldn't open device, some information will be missing
            Device Descriptor:
              bLength                18
              bDescriptorType         1
              bcdUSB               2.00
              bDeviceClass          239 Miscellaneous Device
              bDeviceSubClass         2 ?
              bDeviceProtocol         1 Interface Association
              bMaxPacketSize0        64
              idVendor           0x1871 Aveo Technology Corp.
              idProduct          0x01f0
              bcdDevice            0.0a
              iManufacturer           1
              iProduct                2
              iSerial                 0
              bNumConfigurations      1
              Configuration Descriptor:
                bLength                 9
                bDescriptorType         2
                wTotalLength          419
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
                  iFunction               2
                Interface Descriptor:
                  bLength                 9
                  bDescriptorType         4
                  bInterfaceNumber        0
                  bAlternateSetting       0
                  bNumEndpoints           1
                  bInterfaceClass        14 Video
                  bInterfaceSubClass      1 Video Control
                  bInterfaceProtocol      0
                  iInterface              2
                  VideoControl Interface Descriptor:
                    bLength                13
                    bDescriptorType        36
                    bDescriptorSubtype      1 (HEADER)
                    bcdUVC               1.00
                    wTotalLength           77
                    dwClockFrequency       30.000000MHz
                    bInCollection           1
                    baInterfaceNr( 0)       1
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
                    bLength                 9
                    bDescriptorType        36
                    bDescriptorSubtype      3 (OUTPUT_TERMINAL)
                    bTerminalID             2
                    wTerminalType      0x0101 USB Streaming
                    bAssocTerminal          0
                    bSourceID               4
                    iTerminal               0
                  VideoControl Interface Descriptor:
                    bLength                11
                    bDescriptorType        36
                    bDescriptorSubtype      5 (PROCESSING_UNIT)
                  Warning: Descriptor too short
                    bUnitID                 3
                    bSourceID               1
                    wMaxMultiplier          0
                    bControlSize            2
                    bmControls     0x0000053b
                      Brightness
                      Contrast
                      Saturation
                      Sharpness
                      Gamma
                      Backlight Compensation
                      Power Line Frequency
                    iProcessing             0
                    bmVideoStandards     0x1a
                      NTSC - 525/60
                      SECAM - 625/50
                      NTSC - 625/50
                  VideoControl Interface Descriptor:
                    bLength                26
                    bDescriptorType        36
                    bDescriptorSubtype      6 (EXTENSION_UNIT)
                    bUnitID                 4
                    guidExtensionCode         {52f2b8aa-d18e-7249-8ced-96b17f04408b}
                    bNumControl             1
                    bNrPins                 1
                    baSourceID( 0)          3
                    bControlSize            1
                    bmControls( 0)       0x01
                    iExtension              0
                  Endpoint Descriptor:
                    bLength                 7
                    bDescriptorType         5
                    bEndpointAddress     0x85  EP 5 IN
                    bmAttributes            3
                      Transfer Type            Interrupt
                      Synch Type               None
                      Usage Type               Data
                    wMaxPacketSize     0x0008  1x 8 bytes
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
                    wTotalLength                      215
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
                    bFrameIndex                         2
                    bmCapabilities                   0x00
                      Still image unsupported
                    wWidth                            160
                    wHeight                           120
                    dwMinBitRate                  9216000
                    dwMaxBitRate                  9216000
                    dwMaxVideoFrameBufferSize       38400
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
                    bFrameIndex                         4
                    bmCapabilities                   0x00
                      Still image unsupported
                    wWidth                            176
                    wHeight                           144
                    dwMinBitRate                 12165120
                    dwMaxBitRate                 12165120
                    dwMaxVideoFrameBufferSize       50688
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
                    bLength                            18
                    bDescriptorType                    36
                    bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
                    bEndpointAddress                    0
                    bNumImageSizePatterns               3
                    wWidth( 0)                        640
                    wHeight( 0)                       480
                    wWidth( 1)                        320
                    wHeight( 1)                       240
                    wWidth( 2)                        160
                    wHeight( 2)                       120
                    bNumCompressionPatterns             3
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

```

---

### Post by pdc on 2017-04-01
so this device is supported by the uvc standard [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)        (as shown in the screenshot)

now you just have to do some homework on uvc

you will see there is a mailing list on the uvc page; you may wish to contact them directly; but if you get it all going, if you post back here so folks know how it went

________

this thread mentions installing uvcdynctrl to configure the camera; once it is behaving .....  [http://www.linuxquestions.org/questions/linux-software-2/camera-settings-in-linux-v4l2-or-uvc-drivers-4175525260/](http://www.linuxquestions.org/questions/linux-software-2/camera-settings-in-linux-v4l2-or-uvc-drivers-4175525260/)

also cited is lucvview [http://manpages.ubuntu.com/manpages/precise/man1/luvcview.1.html](http://manpages.ubuntu.com/manpages/precise/man1/luvcview.1.html)[ATTACH=CONFIG]274399[/ATTACH]

---

### Post by Portaro on 2017-04-05
I solve the problem with install the linux-image-extra for my 3.13.0-32 kernel but now I have other problem the DVB-T seems to not work on kaffeine &#8594;
If I remove the linux-image-extra-3.13.0-32-generic kaffeine works if I use the linux-image-extra-3.13.0-32-generic kaffeine dont work .

Message is device not connected but the USB is pluged.

[IMG]https://framapic.org/CDffrQlvxIVL/0yzs7mZeBak4.png[/IMG]

---

### Post by pdc on 2017-04-05
"I solve the problem with install the [SIZE=4][COLOR="#0000FF"]linux-image-extra[/COLOR][/SIZE] for my 3.13.0-32 kernel"

thank you for this; always something new to learn [http://askubuntu.com/questions/153023/what-is-the-linux-image-extra-package-for-and-do-i-need-it](http://askubuntu.com/questions/153023/what-is-the-linux-image-extra-package-for-and-do-i-need-it)

---

### Post by Portaro on 2017-04-06
Solution (provided by Shiba87 on Gnulinuxvagos.es &#8594; [https://gnulinuxvagos.es/topic/6249-la-camera-aveo-usb-no-me-va-bien/](https://gnulinuxvagos.es/topic/6249-la-camera-aveo-usb-no-me-va-bien/)for the problem with DVB-T that is not recognized by kernels 3.13 ... with any linux-image-extra on Ubuntu 14.04 .

To solve the problem and make both hardware camera and DVB-T recognized is :

- install gcc-6 for Liquorix Kernel &#8594; [https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test)

- install Liquorix &#8594; 

> echo "deb [http://liquorix.net/debian](http://liquorix.net/debian) sid main" | sudo tee /etc/apt/sources.list.d/liquorix.list
echo "deb-src [http://liquorix.net/debian](http://liquorix.net/debian) sid main" | sudo tee -a /etc/apt/sources.list.d/liquorix.list
aptitude update
aptitude install liquorix-keyring
aptitude install linux-image-liquorix-amd64

ls /dev/dvb
adapter0 &#8594; OK! DVB-T is active


Reboot and camera is work and the DVB-T on Kaffeine also see pictures in following &#8594;

[IMG]https://framapic.org/WOV1IjyW6pbj/uD779Skfoj5F.png[/IMG]





[IMG]https://framapic.org/QMghputjbDeB/VbsJL5BOFAez.png[/IMG]

Thanks for user Shiba87 I hope that this post help other people with similar problems with usb webcam (Aveo) and DVB-T USB (ID 07ca:a110 AVerMedia Technologies, Inc. ) &#8594; [http://www.avermedia.com/sp/tv_more/product/tv/avertv_volar_hd_2](http://www.avermedia.com/sp/tv_more/product/tv/avertv_volar_hd_2)

Aveo &#8594;
> $ lsusb -D /dev/bus/usb/001/003
Device: ID 1871:01f0 Aveo Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x1871 Aveo Technology Corp.
  idProduct          0x01f0 
  bcdDevice            0.0a
  iManufacturer           1 AVEO Technology Corp.
  iProduct                2 USB2.0 Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          419
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
      iFunction               2 USB2.0 Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              2 USB2.0 Camera
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           77
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
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
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               4
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000053b
          Brightness
          Contrast
          Saturation
          Sharpness
          Gamma
          Backlight Compensation
          Power Line Frequency
        iProcessing             0 
        bmVideoStandards     0x1a
          NTSC - 525/60
          SECAM - 625/50
          NTSC - 625/50
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {52f2b8aa-d18e-7249-8ced-96b17f04408b}
        bNumControl             1
        bNrPins                 1
        baSourceID( 0)          3
        bControlSize            1
        bmControls( 0)       0x01
        iExtension              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
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
        wTotalLength                      215
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
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  9216000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
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
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                 12165120
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
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
        bLength                            18
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               3
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        320
        wHeight( 1)                       240
        wWidth( 2)                        160
        wHeight( 2)                       120
        bNumCompressionPatterns             3
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


DVB-T Avermedia

> $ lsusb -D /dev/bus/usb/003/002
Device: ID 07ca:a110 AVerMedia Technologies, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07ca AVerMedia Technologies, Inc.
  idProduct          0xa110 
  bcdDevice            2.00
  iManufacturer           1 AVerMedia TECHNOLOGIES, Inc.
  iProduct                2 TD110
  iSerial                 3 (error)
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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

### Post by mörgæs on 2017-04-07
Good, please mark the thread 'solved'.

---

