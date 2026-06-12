---
title: "Mouse regularly stops working for a 1-5 seconds"
date: 2012-01-08
forum: Hardware
---

### Post by f0y on 2012-01-08
Hello! I have a weird problem with Logitech M515 wireless mouse on Ubuntu 11.10 64bit (HP Probook 4720s). My mouse connected via Logitech unifying adapter. Mouse stops working (Cursor cannot be moved and buttons does not work too) for about 1-5 second every 5sec-5 minutes. Touchpad always works fine. The same problem occurs on debian with wired mouse but not so often.

I already did a bunch of stuff, but it does not help...
My actions are:
1) Kernel upgraded to 3.2
2) Changed kernel boot parameters to ```
noapic nolapic acpi=force irqpoll pcie_aspm=off
```
3) Tried to change mousepoll interval in usbhid module ([https://wiki.archlinux.org/index.php/Mouse_Polling_Rate](https://wiki.archlinux.org/index.php/Mouse_Polling_Rate)). I had no success because of unifying adapter.
4) Tried to put adapter to different usb slots
5) I checked all log files in /var/log, but cannot find any error messages.
6) Disabled usb legacy support in bios

This is my log files. Help me please.

```
f0y@probook:~$ sudo lsusb -v

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.00
  iManufacturer           3 Linux 3.0.0-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.00
  iManufacturer           3 Linux 3.0.0-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0020 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0103 power enable connect
   Port 5: 0000.0507 highspeed power suspend enable connect
   Port 6: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0020 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0103 power enable connect
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc52b Unifying Receiver
  bcdDevice           12.01
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          4 RQR12.01_B0019
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
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
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     148
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      98
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 004: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x05c8 Cheng Uei Precision Industry Co., Ltd (Foxlink)
  idProduct          0x0403 
  bcdDevice            1.06
  iManufacturer           3 Foxlink
  iProduct                1 HP Webcam [2 MP Fixed]
  iSerial                 2 200909240102
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         1051
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 HP Webcam [2 MP Fixed]
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
      iFunction               5 HP Webcam [2 MP Fixed]
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              5 HP Webcam [2 MP Fixed]
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           78
        dwClockFrequency       15.000000MHz
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
        bmControls           0x00000004
          Auto-Exposure Priority
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                27
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {8ca72912-b447-9440-b0ce-db07386fb938}
        bNumControl             2
        bNrPins                 1
        baSourceID( 0)          1
        bControlSize            2
        bmControls( 0)       0x00
        bmControls( 1)       0x06
        iExtension              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
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
        bLength                            15
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         2
        wTotalLength                      814
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
        bmaControls( 1)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                9
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
        wWidth                           1024
        wHeight                           768
        dwMinBitRate                125829120
        dwMaxBitRate                125829120
        dwMaxVideoFrameBufferSize     1572864
        dwDefaultFrameInterval        1000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                117964800
        dwMaxBitRate                117964800
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                167772160
        dwMaxBitRate                167772160
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1600
        wHeight                           900
        dwMinBitRate                115200000
        dwMaxBitRate                115200000
        dwMaxVideoFrameBufferSize     2880000
        dwDefaultFrameInterval        2000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1600
        wHeight                          1200
        dwMinBitRate                153600000
        dwMaxBitRate                153600000
        dwMaxVideoFrameBufferSize     3840000
        dwDefaultFrameInterval        2000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         9
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
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               8
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        176
        wHeight( 1)                       144
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                       1024
        wHeight( 3)                       768
        wWidth( 4)                       1280
        wHeight( 4)                       720
        wWidth( 5)                       1280
        wHeight( 5)                      1024
        wWidth( 6)                       1600
        wHeight( 6)                       900
        wWidth( 7)                       1600
        wHeight( 7)                      1200
        bNumCompressionPatterns             8
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            56
        bDescriptorType                    36
        bDescriptorSubtype                 14         Invalid desc subtype: 02 09 30 32 34 59 00 00 10 00 80 00 00 aa 00 38 9b 71 32 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 33 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 00 01 00
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 01 00 80 02 e0 01 00 00 65 04 00 00 ca 08 00 60 09 00 15 16 05 00 04 15 16 05 00 80 1a 06 00 20 a1 07 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 02 00 b0 00 90 00 00 d0 5c 00 00 a0 b9 00 00 c6 00 00 15 16 05 00 04 15 16 05 00 80 1a 06 00 20 a1 07 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 03 00 40 01 f0 00 00 40 19 01 00 80 32 02 00 58 02 00 15 16 05 00 04 15 16 05 00 80 1a 06 00 20 a1 07 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 04 00 00 04 00 03 00 00 c0 03 00 00 40 0b 00 00 18 00 2a 2c 0a 00 03 2a 2c 0a 00 40 42 0f 00 80 84 1e 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 05 00 00 05 d0 02 00 00 a3 02 00 00 ca 08 00 20 1c 00 40 42 0f 00 03 40 42 0f 00 80 84 1e 00 d5 dc 32 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 06 00 00 05 00 04 00 00 c0 03 00 00 80 0c 00 00 28 00 40 42 0f 00 03 40 42 0f 00 80 84 1e 00 d5 dc 32 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 07 00 40 06 84 03 00 b0 1e 04 00 f0 9c 09 00 f2 2b 00 5b cc 15 00 03 5b cc 15 00 80 84 1e 00 d5 dc 32 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 08 00 40 06 b0 04 00 40 7e 05 00 40 d1 0c 00 98 3a 00 5b cc 15 00 03 5b cc 15 00 80 84 1e 00 d5 dc 32 00
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 09 00 80 02 e0 01 00 00 65 04 00 00 ca 08 00 60 09 00 15 16 05 00 04 15 16 05 00 80 1a 06 00 20 a1 07 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               8
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        176
        wHeight( 1)                       144
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                       1024
        wHeight( 3)                       768
        wWidth( 4)                       1280
        wHeight( 4)                       720
        wWidth( 5)                       1280
        wHeight( 5)                      1024
        wWidth( 6)                       1600
        wHeight( 6)                       900
        wWidth( 7)                       1600
        wHeight( 7)                      1200
        bNumCompressionPatterns             8
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
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
        wMaxPacketSize     0x0200  1x 512 bytes
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
        wMaxPacketSize     0x0400  1x 1024 bytes
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
        wMaxPacketSize     0x0b00  2x 768 bytes
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
      bAlternateSetting       6
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
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
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

Bus 002 Device 003: ID 148f:1000 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x1000 
  bcdDevice           52.76
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

```

```

f0y@probook:~$ cat /var/log/syslog 
Jan  8 23:29:39 probook kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jan  8 23:29:39 probook rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1042" x-info="http://www.rsyslog.com"] start
Jan  8 23:29:39 probook rsyslogd: rsyslogd's groupid changed to 103
Jan  8 23:29:39 probook rsyslogd: rsyslogd's userid changed to 101
Jan  8 23:29:39 probook rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jan  8 23:29:39 probook kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  8 23:29:39 probook kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  8 23:29:39 probook kernel: [    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
Jan  8 23:29:39 probook kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=4442b26e-50d9-4df2-8697-275ce772e651 ro quiet splash noapic nolapic acpi=force irqpoll pcie_aspm=off vt.handoff=7
Jan  8 23:29:39 probook kernel: [    0.000000] KERNEL supported cpus:
Jan  8 23:29:39 probook kernel: [    0.000000]   Intel GenuineIntel
Jan  8 23:29:39 probook kernel: [    0.000000]   AMD AuthenticAMD
Jan  8 23:29:39 probook kernel: [    0.000000]   Centaur CentaurHauls
Jan  8 23:29:39 probook kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000befcf000 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000befcf000 - 00000000bf6cf000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000bf6cf000 - 00000000bf7cf000 (ACPI NVS)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000bf7cf000 - 00000000bf7ff000 (ACPI data)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000fed19000 - 00000000fed1a000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001fc000000 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 00000001fc000000 - 0000000200000000 (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000]  BIOS-e820: 0000000200000000 - 000000023c000000 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  8 23:29:39 probook kernel: [    0.000000] DMI 2.6 present.
Jan  8 23:29:39 probook kernel: [    0.000000] DMI: Hewlett-Packard HP ProBook 4720s/1411, BIOS 68AZZ Ver. F.0F 02/18/2011
Jan  8 23:29:39 probook kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan  8 23:29:39 probook kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan  8 23:29:39 probook kernel: [    0.000000] No AGP bridge found
Jan  8 23:29:39 probook kernel: [    0.000000] last_pfn = 0x23c000 max_arch_pfn = 0x400000000
Jan  8 23:29:39 probook kernel: [    0.000000] MTRR default type: uncachable
Jan  8 23:29:39 probook kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  8 23:29:39 probook kernel: [    0.000000]   00000-9FFFF write-back
Jan  8 23:29:39 probook kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  8 23:29:39 probook kernel: [    0.000000]   C0000-FFFFF write-protect
Jan  8 23:29:39 probook kernel: [    0.000000] MTRR variable ranges enabled:
Jan  8 23:29:39 probook kernel: [    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
Jan  8 23:29:39 probook kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Jan  8 23:29:39 probook kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Jan  8 23:29:39 probook kernel: [    0.000000]   3 base 100000000 mask F00000000 write-back
Jan  8 23:29:39 probook kernel: [    0.000000]   4 base 200000000 mask FC0000000 write-back
Jan  8 23:29:39 probook kernel: [    0.000000]   5 base 23C000000 mask FFC000000 uncachable
Jan  8 23:29:39 probook kernel: [    0.000000]   6 disabled
Jan  8 23:29:39 probook kernel: [    0.000000]   7 disabled
Jan  8 23:29:39 probook kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan  8 23:29:39 probook kernel: [    0.000000] last_pfn = 0xbf800 max_arch_pfn = 0x400000000
Jan  8 23:29:39 probook kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jan  8 23:29:39 probook kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Jan  8 23:29:39 probook kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf800000
Jan  8 23:29:39 probook kernel: [    0.000000]  0000000000 - 00bf800000 page 2M
Jan  8 23:29:39 probook kernel: [    0.000000] kernel direct mapping tables up to bf800000 @ 1fffc000-20000000
Jan  8 23:29:39 probook kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000023c000000
Jan  8 23:29:39 probook kernel: [    0.000000]  0100000000 - 023c000000 page 2M
Jan  8 23:29:39 probook kernel: [    0.000000] kernel direct mapping tables up to 23c000000 @ befc5000-befcf000
Jan  8 23:29:39 probook kernel: [    0.000000] RAMDISK: 365b4000 - 372d2000
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: RSDP 00000000000fddc0 00024 (v02 HPQOEM)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: XSDT 00000000bf7fe120 0007C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: FACP 00000000bf7fc000 000F4 (v03 HPQOEM 1411     0000000F HP   00000001)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: DSDT 00000000bf7d8000 1EC21 (v02 HPQOEM 1411     00000001 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: FACS 00000000bf77e000 00040
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: HPET 00000000bf7fb000 00038 (v01 HPQOEM 1411     00000001 HP   00000001)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: APIC 00000000bf7fa000 000BC (v01 HPQOEM 1411     00000001 HP   00000001)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: MCFG 00000000bf7f9000 0003C (v01 HPQOEM 1411     00000001 HP   00000001)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: ASF! 00000000bf7f8000 000A0 (v32 HPQOEM 1411     00000001 HP   00000001)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d5000 00135 (v01 HPQOEM SataAhci 00001000 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d4000 00314 (v01 HPQOEM PtidDevc 00001000 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d3000 0005F (v01 HPQOEM   HPQNLP 00000001 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d2000 00A10 (v01  PmRef    CpuPm 00003000 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d1000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: SSDT 00000000bf7d0000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
Jan  8 23:29:39 probook kernel: [    0.000000] No NUMA configuration found
Jan  8 23:29:39 probook kernel: [    0.000000] Faking a node at 0000000000000000-000000023c000000
Jan  8 23:29:39 probook kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000023c000000
Jan  8 23:29:39 probook kernel: [    0.000000]   NODE_DATA [000000023bffb000 - 000000023bffffff]
Jan  8 23:29:39 probook kernel: [    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880233600000-ffff88023a5fffff] on node 0
Jan  8 23:29:39 probook kernel: [    0.000000] Zone PFN ranges:
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan  8 23:29:39 probook kernel: [    0.000000]   Normal   0x00100000 -> 0x0023c000
Jan  8 23:29:39 probook kernel: [    0.000000] Movable zone start PFN for each node
Jan  8 23:29:39 probook kernel: [    0.000000] early_node_map[5] active PFN ranges
Jan  8 23:29:39 probook kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan  8 23:29:39 probook kernel: [    0.000000]     0: 0x00000100 -> 0x000befcf
Jan  8 23:29:39 probook kernel: [    0.000000]     0: 0x000bf7ff -> 0x000bf800
Jan  8 23:29:39 probook kernel: [    0.000000]     0: 0x00100000 -> 0x001fc000
Jan  8 23:29:39 probook kernel: [    0.000000]     0: 0x00200000 -> 0x0023c000
Jan  8 23:29:39 probook kernel: [    0.000000] On node 0 totalpages: 2060127
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA zone: 5 pages reserved
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA zone: 3922 pages, LIFO batch:0
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jan  8 23:29:39 probook kernel: [    0.000000]   DMA32 zone: 763912 pages, LIFO batch:31
Jan  8 23:29:39 probook kernel: [    0.000000]   Normal zone: 17696 pages used for memmap
Jan  8 23:29:39 probook kernel: [    0.000000]   Normal zone: 1260256 pages, LIFO batch:31
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan  8 23:29:39 probook kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan  8 23:29:39 probook kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan  8 23:29:39 probook kernel: [    0.000000] No local APIC present
Jan  8 23:29:39 probook kernel: [    0.000000] APIC: disable apic facility
Jan  8 23:29:39 probook kernel: [    0.000000] APIC: switched to apic NOOP
Jan  8 23:29:39 probook kernel: [    0.000000] nr_irqs_gsi: 16
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000befcf000 - 00000000bf6cf000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000bf6cf000 - 00000000bf7cf000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000bf7cf000 - 00000000bf7ff000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed19000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed19000 - 00000000fed1a000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
Jan  8 23:29:39 probook kernel: [    0.000000] PM: Registered nosave memory: 00000001fc000000 - 0000000200000000
Jan  8 23:29:39 probook kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Jan  8 23:29:39 probook kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  8 23:29:39 probook kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
Jan  8 23:29:39 probook kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023bc00000 s79616 r8192 d22784 u2097152
Jan  8 23:29:39 probook kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u2097152 alloc=1*2097152
Jan  8 23:29:39 probook kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan  8 23:29:39 probook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2028090
Jan  8 23:29:39 probook kernel: [    0.000000] Policy zone: Normal
Jan  8 23:29:39 probook kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=4442b26e-50d9-4df2-8697-275ce772e651 ro quiet splash noapic nolapic acpi=force irqpoll pcie_aspm=off vt.handoff=7
Jan  8 23:29:39 probook kernel: [    0.000000] Misrouted IRQ fixup and polling support enabled
Jan  8 23:29:39 probook kernel: [    0.000000] This may significantly impact system performance
Jan  8 23:29:39 probook kernel: [    0.000000] PCIe ASPM is disabled
Jan  8 23:29:39 probook kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan  8 23:29:39 probook kernel: [    0.000000] Checking aperture...
Jan  8 23:29:39 probook kernel: [    0.000000] No AGP bridge found
Jan  8 23:29:39 probook kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan  8 23:29:39 probook kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan  8 23:29:39 probook kernel: [    0.000000] Memory: 8032640k/9371648k available (6109k kernel code, 1131140k absent, 207868k reserved, 4876k data, 984k init)
Jan  8 23:29:39 probook kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan  8 23:29:39 probook kernel: [    0.000000] Hierarchical RCU implementation.
Jan  8 23:29:39 probook kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan  8 23:29:39 probook kernel: [    0.000000] NR_IRQS:16640 nr_irqs:256 16
Jan  8 23:29:39 probook kernel: [    0.000000] Extended CMOS year: 2000
Jan  8 23:29:39 probook kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan  8 23:29:39 probook kernel: [    0.000000] Console: colour dummy device 80x25
Jan  8 23:29:39 probook kernel: [    0.000000] console [tty0] enabled
Jan  8 23:29:39 probook kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Jan  8 23:29:39 probook kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  8 23:29:39 probook kernel: [    0.000000] hpet clockevent registered
Jan  8 23:29:39 probook kernel: [    0.000000] Fast TSC calibration using PIT
Jan  8 23:29:39 probook kernel: [    0.004000] Detected 2527.056 MHz processor.
Jan  8 23:29:39 probook kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.11 BogoMIPS (lpj=10108224)
Jan  8 23:29:39 probook kernel: [    0.000006] pid_max: default: 32768 minimum: 301
Jan  8 23:29:39 probook kernel: [    0.000030] Security Framework initialized
Jan  8 23:29:39 probook kernel: [    0.000045] AppArmor: AppArmor initialized
Jan  8 23:29:39 probook kernel: [    0.000046] Yama: becoming mindful.
Jan  8 23:29:39 probook kernel: [    0.000772] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jan  8 23:29:39 probook kernel: [    0.002722] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan  8 23:29:39 probook kernel: [    0.003557] Mount-cache hash table entries: 256
Jan  8 23:29:39 probook kernel: [    0.003671] Initializing cgroup subsys cpuacct
Jan  8 23:29:39 probook kernel: [    0.003676] Initializing cgroup subsys memory
Jan  8 23:29:39 probook kernel: [    0.003683] Initializing cgroup subsys devices
Jan  8 23:29:39 probook kernel: [    0.003686] Initializing cgroup subsys freezer
Jan  8 23:29:39 probook kernel: [    0.003687] Initializing cgroup subsys net_cls
Jan  8 23:29:39 probook kernel: [    0.003690] Initializing cgroup subsys blkio
Jan  8 23:29:39 probook kernel: [    0.003694] Initializing cgroup subsys perf_event
Jan  8 23:29:39 probook kernel: [    0.003721] CPU: Physical Processor ID: 0
Jan  8 23:29:39 probook kernel: [    0.003722] CPU: Processor Core ID: 0
Jan  8 23:29:39 probook kernel: [    0.003728] mce: CPU supports 9 MCE banks
Jan  8 23:29:39 probook kernel: [    0.003738] using mwait in idle threads.
Jan  8 23:29:39 probook kernel: [    0.003779] SMP alternatives: switching to UP code
Jan  8 23:29:39 probook kernel: [    0.010826] Freeing SMP alternatives: 24k freed
Jan  8 23:29:39 probook kernel: [    0.010836] ACPI: Core revision 20110413
Jan  8 23:29:39 probook kernel: [    0.019611] ACPI: setting ELCR to 0200 (from 0c20)
Jan  8 23:29:39 probook kernel: [    0.020216] ftrace: allocating 25647 entries in 101 pages
Jan  8 23:29:39 probook kernel: [    0.027496] weird, boot CPU (#0) not listed by the BIOS.
Jan  8 23:29:39 probook kernel: [    0.027499] SMP motherboard not detected.
Jan  8 23:29:39 probook kernel: [    0.027501] Apic disabled
Jan  8 23:29:39 probook kernel: [    0.027502] Local APIC not detected. Using dummy APIC emulation.
Jan  8 23:29:39 probook kernel: [    0.027503] SMP disabled
Jan  8 23:29:39 probook kernel: [    0.027505] Performance Events: PEBS fmt1+, Westmere events, 
Jan  8 23:29:39 probook kernel: [    0.027509] no APIC, boot with the "lapic" boot parameter to force-enable it.
Jan  8 23:29:39 probook kernel: [    0.027510] no hardware sampling interrupt available.
Jan  8 23:29:39 probook kernel: [    0.027513] Intel PMU driver.
Jan  8 23:29:39 probook kernel: [    0.027515] ... version:                3
Jan  8 23:29:39 probook kernel: [    0.027516] ... bit width:              48
Jan  8 23:29:39 probook kernel: [    0.027517] ... generic registers:      4
Jan  8 23:29:39 probook kernel: [    0.027518] ... value mask:             0000ffffffffffff
Jan  8 23:29:39 probook kernel: [    0.027520] ... max period:             000000007fffffff
Jan  8 23:29:39 probook kernel: [    0.027521] ... fixed-purpose events:   3
Jan  8 23:29:39 probook kernel: [    0.027522] ... event mask:             000000070000000f
Jan  8 23:29:39 probook kernel: [    0.027840] Brought up 1 CPUs
Jan  8 23:29:39 probook kernel: [    0.027842] Total of 1 processors activated (5054.11 BogoMIPS).
Jan  8 23:29:39 probook kernel: [    0.027924] devtmpfs: initialized
Jan  8 23:29:39 probook kernel: [    0.028033] PM: Registering ACPI NVS region at bf6cf000 (1048576 bytes)
Jan  8 23:29:39 probook kernel: [    0.029311] print_constraints: dummy: 
Jan  8 23:29:39 probook kernel: [    0.029339] Time: 19:28:52  Date: 01/08/12
Jan  8 23:29:39 probook kernel: [    0.029367] NET: Registered protocol family 16
Jan  8 23:29:39 probook kernel: [    0.029456] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jan  8 23:29:39 probook kernel: [    0.029458] ACPI: bus type pci registered
Jan  8 23:29:39 probook kernel: [    0.029522] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  8 23:29:39 probook kernel: [    0.029525] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jan  8 23:29:39 probook kernel: [    0.061752] PCI: Using configuration type 1 for base access
Jan  8 23:29:39 probook kernel: [    0.062367] bio: create slab <bio-0> at 0
Jan  8 23:29:39 probook kernel: [    0.064169] ACPI: EC: Look up EC in DSDT
Jan  8 23:29:39 probook kernel: [    0.067253] ACPI: Executed 2 blocks of module-level executable AML code
Jan  8 23:29:39 probook kernel: [    0.073360] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan  8 23:29:39 probook kernel: [    0.109994] ACPI: Interpreter enabled
Jan  8 23:29:39 probook kernel: [    0.109998] ACPI: (supports S0 S3 S4 S5)
Jan  8 23:29:39 probook kernel: [    0.110016] ACPI: Using PIC for interrupt routing
Jan  8 23:29:39 probook kernel: [    0.111513] ACPI: Power Resource [APPR] (off)
Jan  8 23:29:39 probook kernel: [    0.115074] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Jan  8 23:29:39 probook kernel: [    0.115261] ACPI: No dock devices found.
Jan  8 23:29:39 probook kernel: [    0.115263] HEST: Table not found.
Jan  8 23:29:39 probook kernel: [    0.115266] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan  8 23:29:39 probook kernel: [    0.115992] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Jan  8 23:29:39 probook kernel: [    0.116599] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jan  8 23:29:39 probook kernel: [    0.116601] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jan  8 23:29:39 probook kernel: [    0.116603] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jan  8 23:29:39 probook kernel: [    0.116606] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
Jan  8 23:29:39 probook kernel: [    0.116608] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
Jan  8 23:29:39 probook kernel: [    0.116610] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
Jan  8 23:29:39 probook kernel: [    0.116622] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.116639] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
Jan  8 23:29:39 probook kernel: [    0.116655] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.116678] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.116681] pci 0000:00:01.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.116727] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
Jan  8 23:29:39 probook kernel: [    0.116755] pci 0000:00:16.0: reg 10: [mem 0xd4604000-0xd460400f 64bit]
Jan  8 23:29:39 probook kernel: [    0.116831] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.116835] pci 0000:00:16.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.116874] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
Jan  8 23:29:39 probook kernel: [    0.116899] pci 0000:00:1a.0: reg 10: [mem 0xd4609000-0xd46093ff]
Jan  8 23:29:39 probook kernel: [    0.116985] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.116989] pci 0000:00:1a.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117018] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
Jan  8 23:29:39 probook kernel: [    0.117039] pci 0000:00:1b.0: reg 10: [mem 0xd4600000-0xd4603fff 64bit]
Jan  8 23:29:39 probook kernel: [    0.117114] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117119] pci 0000:00:1b.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117146] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.117223] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117227] pci 0000:00:1c.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117256] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.117333] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117338] pci 0000:00:1c.1: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117366] pci 0000:00:1c.3: [8086:3b48] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.117444] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117449] pci 0000:00:1c.3: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117477] pci 0000:00:1c.5: [8086:3b4c] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.117554] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117559] pci 0000:00:1c.5: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117594] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
Jan  8 23:29:39 probook kernel: [    0.117618] pci 0000:00:1d.0: reg 10: [mem 0xd4608000-0xd46083ff]
Jan  8 23:29:39 probook kernel: [    0.117703] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.117708] pci 0000:00:1d.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.117732] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jan  8 23:29:39 probook kernel: [    0.117806] pci 0000:00:1f.0: [8086:3b0b] type 0 class 0x000601
Jan  8 23:29:39 probook kernel: [    0.117922] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
Jan  8 23:29:39 probook kernel: [    0.117949] pci 0000:00:1f.2: reg 10: [io  0x6028-0x602f]
Jan  8 23:29:39 probook kernel: [    0.117960] pci 0000:00:1f.2: reg 14: [io  0x6034-0x6037]
Jan  8 23:29:39 probook kernel: [    0.117971] pci 0000:00:1f.2: reg 18: [io  0x6020-0x6027]
Jan  8 23:29:39 probook kernel: [    0.117982] pci 0000:00:1f.2: reg 1c: [io  0x6030-0x6033]
Jan  8 23:29:39 probook kernel: [    0.117993] pci 0000:00:1f.2: reg 20: [io  0x6000-0x601f]
Jan  8 23:29:39 probook kernel: [    0.118004] pci 0000:00:1f.2: reg 24: [mem 0xd4607000-0xd46077ff]
Jan  8 23:29:39 probook kernel: [    0.118051] pci 0000:00:1f.2: PME# supported from D3hot
Jan  8 23:29:39 probook kernel: [    0.118055] pci 0000:00:1f.2: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.118104] pci 0000:01:00.0: [1002:68e4] type 0 class 0x000300
Jan  8 23:29:39 probook kernel: [    0.118120] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.118133] pci 0000:01:00.0: reg 18: [mem 0xd4500000-0xd451ffff 64bit]
Jan  8 23:29:39 probook kernel: [    0.118141] pci 0000:01:00.0: reg 20: [io  0x5000-0x50ff]
Jan  8 23:29:39 probook kernel: [    0.118157] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jan  8 23:29:39 probook kernel: [    0.118174] pci 0000:01:00.0: supports D1 D2
Jan  8 23:29:39 probook kernel: [    0.118193] pci 0000:01:00.1: [1002:aa68] type 0 class 0x000403
Jan  8 23:29:39 probook kernel: [    0.118209] pci 0000:01:00.1: reg 10: [mem 0xd4520000-0xd4523fff 64bit]
Jan  8 23:29:39 probook kernel: [    0.118258] pci 0000:01:00.1: supports D1 D2
Jan  8 23:29:39 probook kernel: [    0.118281] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  8 23:29:39 probook kernel: [    0.118284] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
Jan  8 23:29:39 probook kernel: [    0.118286] pci 0000:00:01.0:   bridge window [mem 0xd4500000-0xd45fffff]
Jan  8 23:29:39 probook kernel: [    0.118290] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.118345] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jan  8 23:29:39 probook kernel: [    0.118350] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Jan  8 23:29:39 probook kernel: [    0.118355] pci 0000:00:1c.0:   bridge window [mem 0xd4400000-0xd44fffff]
Jan  8 23:29:39 probook kernel: [    0.118362] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  8 23:29:39 probook kernel: [    0.118417] pci 0000:00:1c.1: PCI bridge to [bus 03-43]
Jan  8 23:29:39 probook kernel: [    0.118422] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
Jan  8 23:29:39 probook kernel: [    0.118426] pci 0000:00:1c.1:   bridge window [mem 0xd0400000-0xd43fffff]
Jan  8 23:29:39 probook kernel: [    0.118433] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  8 23:29:39 probook kernel: [    0.118529] pci 0000:44:00.0: [1814:3090] type 0 class 0x000280
Jan  8 23:29:39 probook kernel: [    0.118553] pci 0000:44:00.0: reg 10: [mem 0xd0300000-0xd030ffff]
Jan  8 23:29:39 probook kernel: [    0.118740] pci 0000:00:1c.3: PCI bridge to [bus 44-44]
Jan  8 23:29:39 probook kernel: [    0.118745] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
Jan  8 23:29:39 probook kernel: [    0.118750] pci 0000:00:1c.3:   bridge window [mem 0xd0300000-0xd03fffff]
Jan  8 23:29:39 probook kernel: [    0.118757] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  8 23:29:39 probook kernel: [    0.118828] pci 0000:45:00.0: [10ec:8168] type 0 class 0x000200
Jan  8 23:29:39 probook kernel: [    0.118844] pci 0000:45:00.0: reg 10: [io  0x2000-0x20ff]
Jan  8 23:29:39 probook kernel: [    0.118873] pci 0000:45:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.118892] pci 0000:45:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.118906] pci 0000:45:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jan  8 23:29:39 probook kernel: [    0.118944] pci 0000:45:00.0: supports D1 D2
Jan  8 23:29:39 probook kernel: [    0.118946] pci 0000:45:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  8 23:29:39 probook kernel: [    0.118950] pci 0000:45:00.0: PME# disabled
Jan  8 23:29:39 probook kernel: [    0.118987] pci 0000:00:1c.5: PCI bridge to [bus 45-45]
Jan  8 23:29:39 probook kernel: [    0.118991] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Jan  8 23:29:39 probook kernel: [    0.118996] pci 0000:00:1c.5:   bridge window [mem 0xd0200000-0xd02fffff]
Jan  8 23:29:39 probook kernel: [    0.119003] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.119076] pci 0000:00:1e.0: PCI bridge to [bus 46-46] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119080] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Jan  8 23:29:39 probook kernel: [    0.119085] pci 0000:00:1e.0:   bridge window [mem 0xd0100000-0xd01fffff]
Jan  8 23:29:39 probook kernel: [    0.119092] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  8 23:29:39 probook kernel: [    0.119094] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119096] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119098] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119100] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119102] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfedfffff] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119104] pci 0000:00:1e.0:   bridge window [mem 0xfee01000-0xffffffff] (subtractive decode)
Jan  8 23:29:39 probook kernel: [    0.119138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan  8 23:29:39 probook kernel: [    0.119423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Jan  8 23:29:39 probook kernel: [    0.119475] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Jan  8 23:29:39 probook kernel: [    0.119529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jan  8 23:29:39 probook kernel: [    0.119564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jan  8 23:29:39 probook kernel: [    0.119619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jan  8 23:29:39 probook kernel: [    0.119657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Jan  8 23:29:39 probook kernel: [    0.120083]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x19)
Jan  8 23:29:39 probook kernel: [    0.124630] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
Jan  8 23:29:39 probook kernel: [    0.124687] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124704] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124722] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124737] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124752] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124769] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
Jan  8 23:29:39 probook kernel: [    0.124797]  pci0000:ff: Unable to request _OSC control (_OSC support mask: 0x19)
Jan  8 23:29:39 probook kernel: [    0.124981] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan  8 23:29:39 probook kernel: [    0.125020] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Jan  8 23:29:39 probook kernel: [    0.125058] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan  8 23:29:39 probook kernel: [    0.125096] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan  8 23:29:39 probook kernel: [    0.125133] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan  8 23:29:39 probook kernel: [    0.125171] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jan  8 23:29:39 probook kernel: [    0.125209] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Jan  8 23:29:39 probook kernel: [    0.125250] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Jan  8 23:29:39 probook kernel: [    0.125333] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan  8 23:29:39 probook kernel: [    0.125337] vgaarb: loaded
Jan  8 23:29:39 probook kernel: [    0.125338] vgaarb: bridge control possible 0000:01:00.0
Jan  8 23:29:39 probook kernel: [    0.125481] SCSI subsystem initialized
Jan  8 23:29:39 probook kernel: [    0.125522] libata version 3.00 loaded.
Jan  8 23:29:39 probook kernel: [    0.125554] usbcore: registered new interface driver usbfs
Jan  8 23:29:39 probook kernel: [    0.125564] usbcore: registered new interface driver hub
Jan  8 23:29:39 probook kernel: [    0.125583] usbcore: registered new device driver usb
Jan  8 23:29:39 probook kernel: [    0.125648] PCI: Using ACPI for IRQ routing
Jan  8 23:29:39 probook kernel: [    0.135590] PCI: pci_cache_line_size set to 64 bytes
Jan  8 23:29:39 probook kernel: [    0.135658] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jan  8 23:29:39 probook kernel: [    0.135660] reserve RAM buffer: 00000000befcf000 - 00000000bfffffff 
Jan  8 23:29:39 probook kernel: [    0.135662] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
Jan  8 23:29:39 probook kernel: [    0.135740] NetLabel: Initializing
Jan  8 23:29:39 probook kernel: [    0.135741] NetLabel:  domain hash size = 128
Jan  8 23:29:39 probook kernel: [    0.135742] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  8 23:29:39 probook kernel: [    0.135753] NetLabel:  unlabeled traffic allowed by default
Jan  8 23:29:39 probook kernel: [    0.135796] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jan  8 23:29:39 probook kernel: [    0.135801] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jan  8 23:29:39 probook kernel: [    0.137816] Switching to clocksource hpet
Jan  8 23:29:39 probook kernel: [    0.139373] Switched to NOHz mode on CPU #0
Jan  8 23:29:39 probook kernel: [    0.142717] AppArmor: AppArmor Filesystem Enabled
Jan  8 23:29:39 probook kernel: [    0.142748] pnp: PnP ACPI init
Jan  8 23:29:39 probook kernel: [    0.142762] ACPI: bus type pnp registered
Jan  8 23:29:39 probook kernel: [    0.143124] pnp 00:00: [bus 00-fe]
Jan  8 23:29:39 probook kernel: [    0.143127] pnp 00:00: [io  0x0000-0x0cf7 window]
Jan  8 23:29:39 probook kernel: [    0.143128] pnp 00:00: [io  0x0cf8-0x0cff]
Jan  8 23:29:39 probook kernel: [    0.143130] pnp 00:00: [io  0x0d00-0xffff window]
Jan  8 23:29:39 probook kernel: [    0.143132] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jan  8 23:29:39 probook kernel: [    0.143133] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Jan  8 23:29:39 probook kernel: [    0.143135] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Jan  8 23:29:39 probook kernel: [    0.143136] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Jan  8 23:29:39 probook kernel: [    0.143138] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Jan  8 23:29:39 probook kernel: [    0.143140] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jan  8 23:29:39 probook kernel: [    0.143141] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Jan  8 23:29:39 probook kernel: [    0.143143] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Jan  8 23:29:39 probook kernel: [    0.143144] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Jan  8 23:29:39 probook kernel: [    0.143146] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Jan  8 23:29:39 probook kernel: [    0.143148] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Jan  8 23:29:39 probook kernel: [    0.143149] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Jan  8 23:29:39 probook kernel: [    0.143151] pnp 00:00: [mem 0x000ec000-0x000effff window]
Jan  8 23:29:39 probook kernel: [    0.143152] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Jan  8 23:29:39 probook kernel: [    0.143154] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
Jan  8 23:29:39 probook kernel: [    0.143156] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
Jan  8 23:29:39 probook kernel: [    0.143157] pnp 00:00: [mem 0xfee01000-0xffffffff window]
Jan  8 23:29:39 probook kernel: [    0.143246] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jan  8 23:29:39 probook kernel: [    0.143429] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
Jan  8 23:29:39 probook kernel: [    0.143431] pnp 00:01: [mem 0xfed10000-0xfed13fff]
Jan  8 23:29:39 probook kernel: [    0.143432] pnp 00:01: [mem 0xfed1b000-0xfed1bfff]
Jan  8 23:29:39 probook kernel: [    0.143434] pnp 00:01: [mem 0xfed19000-0xfed19fff]
Jan  8 23:29:39 probook kernel: [    0.143435] pnp 00:01: [mem 0xd4700000-0xd4700fff]
Jan  8 23:29:39 probook kernel: [    0.143437] pnp 00:01: [mem 0xe0000000-0xefffffff]
Jan  8 23:29:39 probook kernel: [    0.143438] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Jan  8 23:29:39 probook kernel: [    0.143440] pnp 00:01: [mem 0xfed90000-0xfed8ffff disabled]
Jan  8 23:29:39 probook kernel: [    0.143442] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
Jan  8 23:29:39 probook kernel: [    0.143443] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Jan  8 23:29:39 probook kernel: [    0.143487] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143490] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143492] system 00:01: [mem 0xfed1b000-0xfed1bfff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143494] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143496] system 00:01: [mem 0xd4700000-0xd4700fff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143498] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143500] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143502] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143504] system 00:01: [mem 0xfec00000-0xfec00fff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143507] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  8 23:29:39 probook kernel: [    0.143576] pnp 00:02: [io  0x0000-0x001f]
Jan  8 23:29:39 probook kernel: [    0.143578] pnp 00:02: [io  0x0081-0x0091]
Jan  8 23:29:39 probook kernel: [    0.143579] pnp 00:02: [io  0x0093-0x009f]
Jan  8 23:29:39 probook kernel: [    0.143583] pnp 00:02: [io  0x00c0-0x00df]
Jan  8 23:29:39 probook kernel: [    0.143585] pnp 00:02: [dma 4]
Jan  8 23:29:39 probook kernel: [    0.143609] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jan  8 23:29:39 probook kernel: [    0.143617] pnp 00:03: [mem 0xff000000-0xffffffff]
Jan  8 23:29:39 probook kernel: [    0.143641] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Jan  8 23:29:39 probook kernel: [    0.143672] pnp 00:04: [io  0xfe00-0xfe0f]
Jan  8 23:29:39 probook kernel: [    0.143673] pnp 00:04: [io  0xfe80-0xfe8f]
Jan  8 23:29:39 probook kernel: [    0.143675] pnp 00:04: [mem 0xfed40000-0xfed44fff]
Jan  8 23:29:39 probook kernel: [    0.143711] system 00:04: [io  0xfe00-0xfe0f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143713] system 00:04: [io  0xfe80-0xfe8f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143716] system 00:04: [mem 0xfed40000-0xfed44fff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143718] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  8 23:29:39 probook kernel: [    0.143800] pnp 00:05: [mem 0xfed00000-0xfed003ff]
Jan  8 23:29:39 probook kernel: [    0.143825] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Jan  8 23:29:39 probook kernel: [    0.143834] pnp 00:06: [io  0x00f0]
Jan  8 23:29:39 probook kernel: [    0.143837] pnp 00:06: [irq 13]
Jan  8 23:29:39 probook kernel: [    0.143863] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan  8 23:29:39 probook kernel: [    0.143872] pnp 00:07: [io  0x002e-0x002f]
Jan  8 23:29:39 probook kernel: [    0.143874] pnp 00:07: [io  0x004e-0x004f]
Jan  8 23:29:39 probook kernel: [    0.143875] pnp 00:07: [io  0x0061]
Jan  8 23:29:39 probook kernel: [    0.143876] pnp 00:07: [io  0x0063]
Jan  8 23:29:39 probook kernel: [    0.143877] pnp 00:07: [io  0x0065]
Jan  8 23:29:39 probook kernel: [    0.143879] pnp 00:07: [io  0x0067]
Jan  8 23:29:39 probook kernel: [    0.143880] pnp 00:07: [io  0x0070]
Jan  8 23:29:39 probook kernel: [    0.143881] pnp 00:07: [io  0x0080]
Jan  8 23:29:39 probook kernel: [    0.143882] pnp 00:07: [io  0x0092]
Jan  8 23:29:39 probook kernel: [    0.143884] pnp 00:07: [io  0x00b2-0x00b3]
Jan  8 23:29:39 probook kernel: [    0.143885] pnp 00:07: [io  0x0200-0x027f]
Jan  8 23:29:39 probook kernel: [    0.143887] pnp 00:07: [io  0x1000-0x100f]
Jan  8 23:29:39 probook kernel: [    0.143888] pnp 00:07: [io  0xffff]
Jan  8 23:29:39 probook kernel: [    0.143889] pnp 00:07: [io  0xffff]
Jan  8 23:29:39 probook kernel: [    0.143890] pnp 00:07: [io  0x0400-0x047f]
Jan  8 23:29:39 probook kernel: [    0.143892] pnp 00:07: [io  0x0500-0x057f]
Jan  8 23:29:39 probook kernel: [    0.143893] pnp 00:07: [io  0xef80-0xef9f]
Jan  8 23:29:39 probook kernel: [    0.143933] system 00:07: [io  0x0200-0x027f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143935] system 00:07: [io  0x1000-0x100f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143937] system 00:07: [io  0xffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143939] system 00:07: [io  0xffff] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143941] system 00:07: [io  0x0400-0x047f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143943] system 00:07: [io  0x0500-0x057f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143945] system 00:07: [io  0xef80-0xef9f] has been reserved
Jan  8 23:29:39 probook kernel: [    0.143947] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  8 23:29:39 probook kernel: [    0.143954] pnp 00:08: [io  0x0070-0x0077]
Jan  8 23:29:39 probook kernel: [    0.143956] pnp 00:08: [irq 8]
Jan  8 23:29:39 probook kernel: [    0.143982] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  8 23:29:39 probook kernel: [    0.144075] pnp 00:09: [io  0x0060]
Jan  8 23:29:39 probook kernel: [    0.144076] pnp 00:09: [io  0x0064]
Jan  8 23:29:39 probook kernel: [    0.144078] pnp 00:09: [irq 1]
Jan  8 23:29:39 probook kernel: [    0.144105] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
Jan  8 23:29:39 probook kernel: [    0.144112] pnp 00:0a: [irq 12]
Jan  8 23:29:39 probook kernel: [    0.144138] pnp 00:0a: Plug and Play ACPI device, IDs SYN016a SYN0100 SYN0002 PNP0f13 (active)
Jan  8 23:29:39 probook kernel: [    0.144336] pnp 00:0b: [irq 23]
Jan  8 23:29:39 probook kernel: [    0.144368] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
Jan  8 23:29:39 probook kernel: [    0.144485] pnp 00:0c: [bus ff]
Jan  8 23:29:39 probook kernel: [    0.144520] pnp 00:0c: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan  8 23:29:39 probook kernel: [    0.144604] pnp: PnP ACPI: found 13 devices
Jan  8 23:29:39 probook kernel: [    0.144605] ACPI: ACPI bus type pnp unregistered
Jan  8 23:29:39 probook kernel: [    0.150234] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jan  8 23:29:39 probook kernel: [    0.150238] pci 0000:45:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jan  8 23:29:39 probook kernel: [    0.150245] PCI: max bus depth: 1 pci_try_num: 2
Jan  8 23:29:39 probook kernel: [    0.150299] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd4800000-0xd49fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150302] pci 0000:01:00.0: BAR 6: assigned [mem 0xd4540000-0xd455ffff pref]
Jan  8 23:29:39 probook kernel: [    0.150304] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  8 23:29:39 probook kernel: [    0.150306] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
Jan  8 23:29:39 probook kernel: [    0.150309] pci 0000:00:01.0:   bridge window [mem 0xd4500000-0xd45fffff]
Jan  8 23:29:39 probook kernel: [    0.150312] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150315] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jan  8 23:29:39 probook kernel: [    0.150317] pci 0000:00:1c.0:   bridge window [io  disabled]
Jan  8 23:29:39 probook kernel: [    0.150323] pci 0000:00:1c.0:   bridge window [mem 0xd4400000-0xd44fffff]
Jan  8 23:29:39 probook kernel: [    0.150328] pci 0000:00:1c.0:   bridge window [mem pref disabled]
Jan  8 23:29:39 probook kernel: [    0.150335] pci 0000:00:1c.1: PCI bridge to [bus 03-43]
Jan  8 23:29:39 probook kernel: [    0.150338] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
Jan  8 23:29:39 probook kernel: [    0.150344] pci 0000:00:1c.1:   bridge window [mem 0xd0400000-0xd43fffff]
Jan  8 23:29:39 probook kernel: [    0.150349] pci 0000:00:1c.1:   bridge window [mem 0xd4800000-0xd49fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150356] pci 0000:00:1c.3: PCI bridge to [bus 44-44]
Jan  8 23:29:39 probook kernel: [    0.150357] pci 0000:00:1c.3:   bridge window [io  disabled]
Jan  8 23:29:39 probook kernel: [    0.150363] pci 0000:00:1c.3:   bridge window [mem 0xd0300000-0xd03fffff]
Jan  8 23:29:39 probook kernel: [    0.150368] pci 0000:00:1c.3:   bridge window [mem pref disabled]
Jan  8 23:29:39 probook kernel: [    0.150376] pci 0000:45:00.0: BAR 6: assigned [mem 0xd0020000-0xd003ffff pref]
Jan  8 23:29:39 probook kernel: [    0.150378] pci 0000:00:1c.5: PCI bridge to [bus 45-45]
Jan  8 23:29:39 probook kernel: [    0.150381] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Jan  8 23:29:39 probook kernel: [    0.150387] pci 0000:00:1c.5:   bridge window [mem 0xd0200000-0xd02fffff]
Jan  8 23:29:39 probook kernel: [    0.150392] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150399] pci 0000:00:1e.0: PCI bridge to [bus 46-46]
Jan  8 23:29:39 probook kernel: [    0.150400] pci 0000:00:1e.0:   bridge window [io  disabled]
Jan  8 23:29:39 probook kernel: [    0.150406] pci 0000:00:1e.0:   bridge window [mem 0xd0100000-0xd01fffff]
Jan  8 23:29:39 probook kernel: [    0.150410] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Jan  8 23:29:39 probook kernel: [    0.150477] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Jan  8 23:29:39 probook kernel: [    0.150480] PCI: setting IRQ 10 as level-triggered
Jan  8 23:29:39 probook kernel: [    0.150485] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [    0.150488] pci 0000:00:01.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150541] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Jan  8 23:29:39 probook kernel: [    0.150542] PCI: setting IRQ 5 as level-triggered
Jan  8 23:29:39 probook kernel: [    0.150547] pci 0000:00:1c.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan  8 23:29:39 probook kernel: [    0.150552] pci 0000:00:1c.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150560] pci 0000:00:1c.1: PCI INT B -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [    0.150564] pci 0000:00:1c.1: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150616] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jan  8 23:29:39 probook kernel: [    0.150617] PCI: setting IRQ 11 as level-triggered
Jan  8 23:29:39 probook kernel: [    0.150622] pci 0000:00:1c.3: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jan  8 23:29:39 probook kernel: [    0.150627] pci 0000:00:1c.3: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150635] pci 0000:00:1c.5: PCI INT B -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [    0.150639] pci 0000:00:1c.5: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150647] pci 0000:00:1e.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.150651] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan  8 23:29:39 probook kernel: [    0.150653] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan  8 23:29:39 probook kernel: [    0.150655] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan  8 23:29:39 probook kernel: [    0.150657] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xdfffffff]
Jan  8 23:29:39 probook kernel: [    0.150658] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
Jan  8 23:29:39 probook kernel: [    0.150660] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
Jan  8 23:29:39 probook kernel: [    0.150662] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Jan  8 23:29:39 probook kernel: [    0.150664] pci_bus 0000:01: resource 1 [mem 0xd4500000-0xd45fffff]
Jan  8 23:29:39 probook kernel: [    0.150666] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150668] pci_bus 0000:02: resource 1 [mem 0xd4400000-0xd44fffff]
Jan  8 23:29:39 probook kernel: [    0.150670] pci_bus 0000:03: resource 0 [io  0x3000-0x4fff]
Jan  8 23:29:39 probook kernel: [    0.150671] pci_bus 0000:03: resource 1 [mem 0xd0400000-0xd43fffff]
Jan  8 23:29:39 probook kernel: [    0.150673] pci_bus 0000:03: resource 2 [mem 0xd4800000-0xd49fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150675] pci_bus 0000:44: resource 1 [mem 0xd0300000-0xd03fffff]
Jan  8 23:29:39 probook kernel: [    0.150677] pci_bus 0000:45: resource 0 [io  0x2000-0x2fff]
Jan  8 23:29:39 probook kernel: [    0.150679] pci_bus 0000:45: resource 1 [mem 0xd0200000-0xd02fffff]
Jan  8 23:29:39 probook kernel: [    0.150681] pci_bus 0000:45: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
Jan  8 23:29:39 probook kernel: [    0.150683] pci_bus 0000:46: resource 1 [mem 0xd0100000-0xd01fffff]
Jan  8 23:29:39 probook kernel: [    0.150684] pci_bus 0000:46: resource 4 [io  0x0000-0x0cf7]
Jan  8 23:29:39 probook kernel: [    0.150686] pci_bus 0000:46: resource 5 [io  0x0d00-0xffff]
Jan  8 23:29:39 probook kernel: [    0.150688] pci_bus 0000:46: resource 6 [mem 0x000a0000-0x000bffff]
Jan  8 23:29:39 probook kernel: [    0.150690] pci_bus 0000:46: resource 7 [mem 0xc0000000-0xdfffffff]
Jan  8 23:29:39 probook kernel: [    0.150691] pci_bus 0000:46: resource 8 [mem 0xf0000000-0xfedfffff]
Jan  8 23:29:39 probook kernel: [    0.150693] pci_bus 0000:46: resource 9 [mem 0xfee01000-0xffffffff]
Jan  8 23:29:39 probook kernel: [    0.150726] NET: Registered protocol family 2
Jan  8 23:29:39 probook kernel: [    0.150908] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan  8 23:29:39 probook kernel: [    0.151865] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan  8 23:29:39 probook kernel: [    0.153501] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan  8 23:29:39 probook kernel: [    0.153711] TCP: Hash tables configured (established 524288 bind 65536)
Jan  8 23:29:39 probook kernel: [    0.153712] TCP reno registered
Jan  8 23:29:39 probook kernel: [    0.153726] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jan  8 23:29:39 probook kernel: [    0.153761] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jan  8 23:29:39 probook kernel: [    0.153907] NET: Registered protocol family 1
Jan  8 23:29:39 probook kernel: [    0.154001] pci 0000:01:00.0: Boot video device
Jan  8 23:29:39 probook kernel: [    0.154020] PCI: CLS 64 bytes, default 64
Jan  8 23:29:39 probook kernel: [    0.154036] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan  8 23:29:39 probook kernel: [    0.154038] Placing 64MB software IO TLB between ffff8800bafc5000 - ffff8800befc5000
Jan  8 23:29:39 probook kernel: [    0.154040] software IO TLB at phys 0xbafc5000 - 0xbefc5000
Jan  8 23:29:39 probook kernel: [    0.154346] audit: initializing netlink socket (disabled)
Jan  8 23:29:39 probook kernel: [    0.154355] type=2000 audit(1326050932.152:1): initialized
Jan  8 23:29:39 probook kernel: [    0.172923] Trying to unpack rootfs image as initramfs...
Jan  8 23:29:39 probook kernel: [    0.225875] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  8 23:29:39 probook kernel: [    0.285999] VFS: Disk quotas dquot_6.5.2
Jan  8 23:29:39 probook kernel: [    0.286051] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan  8 23:29:39 probook kernel: [    0.289809] fuse init (API version 7.16)
Jan  8 23:29:39 probook kernel: [    0.289889] msgmni has been set to 15688
Jan  8 23:29:39 probook kernel: [    0.301883] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan  8 23:29:39 probook kernel: [    0.301906] io scheduler noop registered
Jan  8 23:29:39 probook kernel: [    0.301908] io scheduler deadline registered
Jan  8 23:29:39 probook kernel: [    0.301945] io scheduler cfq registered (default)
Jan  8 23:29:39 probook kernel: [    0.302047] pcieport 0000:00:01.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.302332] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  8 23:29:39 probook kernel: [    0.302349] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  8 23:29:39 probook kernel: [    0.302384] intel_idle: MWAIT substates: 0x1120
Jan  8 23:29:39 probook kernel: [    0.302386] intel_idle: v0.4 model 0x25
Jan  8 23:29:39 probook kernel: [    0.302387] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan  8 23:29:39 probook kernel: [    0.302547] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jan  8 23:29:39 probook kernel: [    0.302630] ACPI: AC Adapter [AC] (on-line)
Jan  8 23:29:39 probook kernel: [    0.302687] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
Jan  8 23:29:39 probook kernel: [    0.302693] ACPI: Sleep Button [SLPB]
Jan  8 23:29:39 probook kernel: [    0.302723] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jan  8 23:29:39 probook kernel: [    0.302746] ACPI: Lid Switch [LID]
Jan  8 23:29:39 probook kernel: [    0.302774] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan  8 23:29:39 probook kernel: [    0.302777] ACPI: Power Button [PWRF]
Jan  8 23:29:39 probook kernel: [    0.302801] ACPI: acpi_idle yielding to intel_idle
Jan  8 23:29:39 probook kernel: [    0.314650] thermal LNXTHERM:00: registered as thermal_zone0
Jan  8 23:29:39 probook kernel: [    0.314653] ACPI: Thermal Zone [EXTZ] (68 C)
Jan  8 23:29:39 probook kernel: [    0.314690] thermal LNXTHERM:01: registered as thermal_zone1
Jan  8 23:29:39 probook kernel: [    0.314691] ACPI: Thermal Zone [EX2Z] (0 C)
Jan  8 23:29:39 probook kernel: [    0.314730] thermal LNXTHERM:02: registered as thermal_zone2
Jan  8 23:29:39 probook kernel: [    0.314731] ACPI: Thermal Zone [PWMZ] (0 C)
Jan  8 23:29:39 probook kernel: [    0.317302] thermal LNXTHERM:03: registered as thermal_zone3
Jan  8 23:29:39 probook kernel: [    0.317304] ACPI: Thermal Zone [LOCZ] (53 C)
Jan  8 23:29:39 probook kernel: [    0.317700] thermal LNXTHERM:04: registered as thermal_zone4
Jan  8 23:29:39 probook kernel: [    0.317702] ACPI: Thermal Zone [GFXZ] (0 C)
Jan  8 23:29:39 probook kernel: [    0.332007] thermal LNXTHERM:05: registered as thermal_zone5
Jan  8 23:29:39 probook kernel: [    0.332010] ACPI: Thermal Zone [BATZ] (35 C)
Jan  8 23:29:39 probook kernel: [    0.341872] thermal LNXTHERM:06: registered as thermal_zone6
Jan  8 23:29:39 probook kernel: [    0.341875] ACPI: Thermal Zone [EGXZ] (0 C)
Jan  8 23:29:39 probook kernel: [    0.342079] thermal LNXTHERM:07: registered as thermal_zone7
Jan  8 23:29:39 probook kernel: [    0.342081] ACPI: Thermal Zone [CPUZ] (65 C)
Jan  8 23:29:39 probook kernel: [    0.342232] thermal LNXTHERM:08: registered as thermal_zone8
Jan  8 23:29:39 probook kernel: [    0.342234] ACPI: Thermal Zone [MCHZ] (62 C)
Jan  8 23:29:39 probook kernel: [    0.342379] thermal LNXTHERM:09: registered as thermal_zone9
Jan  8 23:29:39 probook kernel: [    0.342381] ACPI: Thermal Zone [PCHZ] (68 C)
Jan  8 23:29:39 probook kernel: [    0.342422] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jan  8 23:29:39 probook kernel: [    0.342439] ERST: Table is not found!
Jan  8 23:29:39 probook kernel: [    0.342511] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  8 23:29:39 probook kernel: [    0.343457] Linux agpgart interface v0.103
Jan  8 23:29:39 probook kernel: [    0.344318] brd: module loaded
Jan  8 23:29:39 probook kernel: [    0.344674] loop: module loaded
Jan  8 23:29:39 probook kernel: [    0.344994] Fixed MDIO Bus: probed
Jan  8 23:29:39 probook kernel: [    0.345011] PPP generic driver version 2.4.2
Jan  8 23:29:39 probook kernel: [    0.345043] tun: Universal TUN/TAP device driver, 1.6
Jan  8 23:29:39 probook kernel: [    0.345045] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  8 23:29:39 probook kernel: [    0.345101] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  8 23:29:39 probook kernel: [    0.345121] ehci_hcd 0000:00:1a.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [    0.345137] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.345141] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jan  8 23:29:39 probook kernel: [    0.345169] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan  8 23:29:39 probook kernel: [    0.345202] ehci_hcd 0000:00:1a.0: debug port 2
Jan  8 23:29:39 probook kernel: [    0.349114] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Jan  8 23:29:39 probook kernel: [    0.354574] ehci_hcd 0000:00:1a.0: irq 10, io mem 0xd4609000
Jan  8 23:29:39 probook kernel: [    0.373864] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jan  8 23:29:39 probook kernel: [    0.374029] hub 1-0:1.0: USB hub found
Jan  8 23:29:39 probook kernel: [    0.374034] hub 1-0:1.0: 2 ports detected
Jan  8 23:29:39 probook kernel: [    0.374175] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Jan  8 23:29:39 probook kernel: [    0.374179] ehci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [    0.374210] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.374213] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jan  8 23:29:39 probook kernel: [    0.374250] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  8 23:29:39 probook kernel: [    0.374280] ehci_hcd 0000:00:1d.0: debug port 2
Jan  8 23:29:39 probook kernel: [    0.378208] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Jan  8 23:29:39 probook kernel: [    0.381883] ehci_hcd 0000:00:1d.0: irq 10, io mem 0xd4608000
Jan  8 23:29:39 probook kernel: [    0.397870] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jan  8 23:29:39 probook kernel: [    0.397993] hub 2-0:1.0: USB hub found
Jan  8 23:29:39 probook kernel: [    0.397998] hub 2-0:1.0: 2 ports detected
Jan  8 23:29:39 probook kernel: [    0.398063] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  8 23:29:39 probook kernel: [    0.398075] uhci_hcd: USB Universal Host Controller Interface driver
Jan  8 23:29:39 probook kernel: [    0.398146] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  8 23:29:39 probook kernel: [    0.400017] i8042: Detected active multiplexing controller, rev 1.1
Jan  8 23:29:39 probook kernel: [    0.400826] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  8 23:29:39 probook kernel: [    0.400832] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan  8 23:29:39 probook kernel: [    0.401549] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan  8 23:29:39 probook kernel: [    0.401571] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan  8 23:29:39 probook kernel: [    0.401587] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan  8 23:29:39 probook kernel: [    0.401704] mousedev: PS/2 mouse device common for all mice
Jan  8 23:29:39 probook kernel: [    0.401818] rtc_cmos 00:08: RTC can wake from S4
Jan  8 23:29:39 probook kernel: [    0.401947] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Jan  8 23:29:39 probook kernel: [    0.401970] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan  8 23:29:39 probook kernel: [    0.402053] device-mapper: uevent: version 1.0.3
Jan  8 23:29:39 probook kernel: [    0.402108] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Jan  8 23:29:39 probook kernel: [    0.402139] cpuidle: using governor ladder
Jan  8 23:29:39 probook kernel: [    0.402169] cpuidle: using governor menu
Jan  8 23:29:39 probook kernel: [    0.402171] EFI Variables Facility v0.08 2004-May-17
Jan  8 23:29:39 probook kernel: [    0.402374] TCP cubic registered
Jan  8 23:29:39 probook kernel: [    0.402471] NET: Registered protocol family 10
Jan  8 23:29:39 probook kernel: [    0.404967] NET: Registered protocol family 17
Jan  8 23:29:39 probook kernel: [    0.404981] Registering the dns_resolver key type
Jan  8 23:29:39 probook kernel: [    0.405058] PM: Hibernation image not present or could not be loaded.
Jan  8 23:29:39 probook kernel: [    0.405068] registered taskstats version 1
Jan  8 23:29:39 probook kernel: [    0.422972] ACPI: Battery Slot [BAT0] (battery present)
Jan  8 23:29:39 probook kernel: [    0.439573] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan  8 23:29:39 probook kernel: [    0.505806] Freeing initrd memory: 13432k freed
Jan  8 23:29:39 probook kernel: [    0.513244]   Magic number: 12:510:495
Jan  8 23:29:39 probook kernel: [    0.513368] rtc_cmos 00:08: setting system clock to 2012-01-08 19:28:53 UTC (1326050933)
Jan  8 23:29:39 probook kernel: [    0.513385] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  8 23:29:39 probook kernel: [    0.513386] EDD information not available.
Jan  8 23:29:39 probook kernel: [    0.514988] Freeing unused kernel memory: 984k freed
Jan  8 23:29:39 probook kernel: [    0.515196] Write protecting the kernel read-only data: 10240k
Jan  8 23:29:39 probook kernel: [    0.515337] Freeing unused kernel memory: 16k freed
Jan  8 23:29:39 probook kernel: [    0.519129] Freeing unused kernel memory: 1396k freed
Jan  8 23:29:39 probook kernel: [    0.605908] ahci 0000:00:1f.2: version 3.0
Jan  8 23:29:39 probook kernel: [    0.606009] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
Jan  8 23:29:39 probook kernel: [    0.606013] ahci 0000:00:1f.2: PCI INT B -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
Jan  8 23:29:39 probook kernel: [    0.606099] ahci: SSS flag set, parallel bus scan disabled
Jan  8 23:29:39 probook kernel: [    0.606140] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
Jan  8 23:29:39 probook kernel: [    0.606143] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
Jan  8 23:29:39 probook kernel: [    0.606149] ahci 0000:00:1f.2: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.619960] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan  8 23:29:39 probook kernel: [    0.619983] r8169 0000:45:00.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan  8 23:29:39 probook kernel: [    0.620024] r8169 0000:45:00.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [    0.620076] r8169 0000:45:00.0: no MSI. Back to INTx.
Jan  8 23:29:39 probook kernel: [    0.620436] r8169 0000:45:00.0: eth0: RTL8168d/8111d at 0xffffc90000c7c000, 64:31:50:09:1a:77, XID 083000c0 IRQ 5
Jan  8 23:29:39 probook kernel: [    0.632464] scsi0 : ahci
Jan  8 23:29:39 probook kernel: [    0.635501] scsi1 : ahci
Jan  8 23:29:39 probook kernel: [    0.638963] scsi2 : ahci
Jan  8 23:29:39 probook kernel: [    0.641683] scsi3 : ahci
Jan  8 23:29:39 probook kernel: [    0.643978] scsi4 : ahci
Jan  8 23:29:39 probook kernel: [    0.645583] scsi5 : ahci
Jan  8 23:29:39 probook kernel: [    0.645788] ata1: SATA max UDMA/133 abar m2048@0xd4607000 port 0xd4607100 irq 11
Jan  8 23:29:39 probook kernel: [    0.645792] ata2: SATA max UDMA/133 abar m2048@0xd4607000 port 0xd4607180 irq 11
Jan  8 23:29:39 probook kernel: [    0.645794] ata3: DUMMY
Jan  8 23:29:39 probook kernel: [    0.645795] ata4: DUMMY
Jan  8 23:29:39 probook kernel: [    0.645797] ata5: SATA max UDMA/133 abar m2048@0xd4607000 port 0xd4607300 irq 11
Jan  8 23:29:39 probook kernel: [    0.645799] ata6: DUMMY
Jan  8 23:29:39 probook kernel: [    0.685557] usb 1-1: new high speed USB device number 2 using ehci_hcd
Jan  8 23:29:39 probook kernel: [    0.818193] hub 1-1:1.0: USB hub found
Jan  8 23:29:39 probook kernel: [    0.818286] hub 1-1:1.0: 6 ports detected
Jan  8 23:29:39 probook kernel: [    0.929434] usb 2-1: new high speed USB device number 2 using ehci_hcd
Jan  8 23:29:39 probook kernel: [    0.965414] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 23:29:39 probook kernel: [    0.971500] ata1.00: unexpected _GTF length (8)
Jan  8 23:29:39 probook kernel: [    0.971576] ata1.00: ATA-8: SAMSUNG HM641JI, 2AJ10003, max UDMA/133
Jan  8 23:29:39 probook kernel: [    0.971582] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jan  8 23:29:39 probook kernel: [    0.977685] ata1.00: unexpected _GTF length (8)
Jan  8 23:29:39 probook kernel: [    0.977766] ata1.00: configured for UDMA/133
Jan  8 23:29:39 probook kernel: [    0.977863] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM641JI  2AJ1 PQ: 0 ANSI: 5
Jan  8 23:29:39 probook kernel: [    0.977971] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  8 23:29:39 probook kernel: [    0.978063] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jan  8 23:29:39 probook kernel: [    0.978099] sd 0:0:0:0: [sda] Write Protect is off
Jan  8 23:29:39 probook kernel: [    0.978101] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  8 23:29:39 probook kernel: [    0.978116] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  8 23:29:39 probook kernel: [    1.055647]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Jan  8 23:29:39 probook kernel: [    1.055933] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  8 23:29:39 probook kernel: [    1.062053] hub 2-1:1.0: USB hub found
Jan  8 23:29:39 probook kernel: [    1.062153] hub 2-1:1.0: 8 ports detected
Jan  8 23:29:39 probook kernel: [    1.133375] usb 1-1.4: new full speed USB device number 3 using ehci_hcd
Jan  8 23:29:39 probook kernel: [    1.169285] Refined TSC clocksource calibration: 2526.982 MHz.
Jan  8 23:29:39 probook kernel: [    1.169293] Switching to clocksource tsc
Jan  8 23:29:39 probook kernel: [    1.297222] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan  8 23:29:39 probook kernel: [    1.299344] ata2.00: unexpected _GTF length (8)
Jan  8 23:29:39 probook kernel: [    1.299348] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0300, max UDMA/100
Jan  8 23:29:39 probook kernel: [    1.301287] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
Jan  8 23:29:39 probook kernel: [    1.301728] ata2.00: unexpected _GTF length (8)
Jan  8 23:29:39 probook kernel: [    1.301736] ata2.00: configured for UDMA/100
Jan  8 23:29:39 probook kernel: [    1.305166] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0300 PQ: 0 ANSI: 5
Jan  8 23:29:39 probook kernel: [    1.310509] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan  8 23:29:39 probook kernel: [    1.310516] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  8 23:29:39 probook kernel: [    1.310643] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan  8 23:29:39 probook kernel: [    1.310691] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  8 23:29:39 probook kernel: [    1.334078] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input4
Jan  8 23:29:39 probook kernel: [    1.334226] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.4/input0
Jan  8 23:29:39 probook kernel: [    1.336153] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input5
Jan  8 23:29:39 probook kernel: [    1.336479] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.4/input1
Jan  8 23:29:39 probook kernel: [    1.340047] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.4/input2
Jan  8 23:29:39 probook kernel: [    1.340163] usbcore: registered new interface driver usbhid
Jan  8 23:29:39 probook kernel: [    1.340165] usbhid: USB HID core driver
Jan  8 23:29:39 probook kernel: [    1.629035] ata5: SATA link down (SStatus 0 SControl 300)
Jan  8 23:29:39 probook kernel: [    2.656657] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
Jan  8 23:29:39 probook kernel: [    2.691077] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jan  8 23:29:39 probook kernel: [   16.130403] mei: module is from the staging directory, the quality is unknown, you have been warned.
Jan  8 23:29:39 probook kernel: [   16.135630] lp: driver loaded but no devices found
Jan  8 23:29:39 probook kernel: [   16.144397] Adding 8103932k swap on /dev/sda5.  Priority:-1 extents:1 across:8103932k 
Jan  8 23:29:39 probook kernel: [   16.160181] mei 0000:00:16.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [   16.160189] mei 0000:00:16.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [   16.272969] cfg80211: Calling CRDA to update world regulatory domain
Jan  8 23:29:39 probook kernel: [   16.281720] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan  8 23:29:39 probook kernel: [   16.281723] Disabling lock debugging due to kernel taint
Jan  8 23:29:39 probook kernel: [   16.352228] wmi: Mapper loaded
Jan  8 23:29:39 probook kernel: [   16.448342] rt2800pci 0000:44:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jan  8 23:29:39 probook kernel: [   16.448353] rt2800pci 0000:44:00.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [   16.453395] type=1400 audit(1326050949.444:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   16.453715] type=1400 audit(1326050949.444:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   16.453919] type=1400 audit(1326050949.444:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   16.481266] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan  8 23:29:39 probook kernel: [   16.481789] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481791] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481793] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481796] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481797] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481799] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481801] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481803] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481805] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481807] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481808] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481810] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481812] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481814] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481816] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481818] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481819] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481821] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481823] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481825] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481827] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481829] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481830] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481832] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481834] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481836] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.481838] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   16.481840] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   16.489234] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jan  8 23:29:39 probook kernel: [   16.504117] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan  8 23:29:39 probook kernel: [   16.509227] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan  8 23:29:39 probook kernel: [   16.518324] Registered led device: rt2800pci-phy0::radio
Jan  8 23:29:39 probook kernel: [   16.518396] Registered led device: rt2800pci-phy0::assoc
Jan  8 23:29:39 probook kernel: [   16.518431] Registered led device: rt2800pci-phy0::quality
Jan  8 23:29:39 probook kernel: [   16.552565] hp_accel: laptop model unknown, using default axes configuration
Jan  8 23:29:39 probook kernel: [   16.553444] lis3lv02d: 8 bits sensor found
Jan  8 23:29:39 probook kernel: [   16.617303] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Jan  8 23:29:39 probook kernel: [   16.667857] acpi device:04: registered as cooling_device1
Jan  8 23:29:39 probook kernel: [   16.668843] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  8 23:29:39 probook kernel: [   16.668851] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  8 23:29:39 probook kernel: [   16.668861] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan  8 23:29:39 probook kernel: [   16.668952] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [   16.701855] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
Jan  8 23:29:39 probook kernel: [   16.701940] lis3lv02d: Cannot get IRQ
Jan  8 23:29:39 probook kernel: [   16.701976] Registered led device: hp::hddprotect
Jan  8 23:29:39 probook kernel: [   16.702007] hp_accel: driver loaded
Jan  8 23:29:39 probook kernel: [   16.702444] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:00/input/input6
Jan  8 23:29:39 probook kernel: [   16.702506] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Jan  8 23:29:39 probook kernel: [   16.904585] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jan  8 23:29:39 probook kernel: [   16.904699] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jan  8 23:29:39 probook kernel: [   16.904971] HDA Intel 0000:01:00.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Jan  8 23:29:39 probook kernel: [   16.905052] HDA Intel 0000:01:00.1: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [   16.905127] Linux video capture interface: v2.00
Jan  8 23:29:39 probook kernel: [   16.915485] [fglrx] Maximum main memory to use for locked dma buffers: 7628 MBytes.
Jan  8 23:29:39 probook kernel: [   16.915638] [fglrx]   vendor: 1002 device: 68e4 count: 1
Jan  8 23:29:39 probook kernel: [   16.915898] [fglrx] ioport: bar 4, base 0x5000, size: 0x100
Jan  8 23:29:39 probook kernel: [   16.915912] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan  8 23:29:39 probook kernel: [   16.915917] pci 0000:01:00.0: setting latency timer to 64
Jan  8 23:29:39 probook kernel: [   16.916053] [fglrx] Kernel PAT support is enabled
Jan  8 23:29:39 probook kernel: [   16.916073] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
Jan  8 23:29:39 probook kernel: [   16.921249] uvcvideo: Found UVC 1.00 device HP Webcam [2 MP Fixed] (05c8:0403)
Jan  8 23:29:39 probook kernel: [   16.923504] spurious 8259A interrupt: IRQ7.
Jan  8 23:29:39 probook kernel: [   16.941998] input: HP Webcam [2 MP Fixed] as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input10
Jan  8 23:29:39 probook kernel: [   16.942092] usbcore: registered new interface driver uvcvideo
Jan  8 23:29:39 probook kernel: [   16.942094] USB Video Class driver (v1.1.0)
Jan  8 23:29:39 probook kernel: [   16.985699] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
Jan  8 23:29:39 probook kernel: [   16.985936] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
Jan  8 23:29:39 probook kernel: [   16.993594] Bluetooth: Core ver 2.16
Jan  8 23:29:39 probook kernel: [   16.996443] NET: Registered protocol family 31
Jan  8 23:29:39 probook kernel: [   16.996445] Bluetooth: HCI device and connection manager initialized
Jan  8 23:29:39 probook kernel: [   16.996448] Bluetooth: HCI socket layer initialized
Jan  8 23:29:39 probook kernel: [   16.996449] Bluetooth: L2CAP socket layer initialized
Jan  8 23:29:39 probook kernel: [   16.998692] Bluetooth: SCO socket layer initialized
Jan  8 23:29:39 probook kernel: [   16.999852] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jan  8 23:29:39 probook kernel: [   17.007387] usbcore: registered new interface driver btusb
Jan  8 23:29:39 probook kernel: [   17.054923] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan  8 23:29:39 probook kernel: [   17.088711] input: HP WMI hotkeys as /devices/virtual/input/input12
Jan  8 23:29:39 probook kernel: [   17.103861] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103864] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103866] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103869] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103870] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103873] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103874] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103876] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103878] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103880] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103882] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103884] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103885] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103887] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103889] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103891] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103893] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103895] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103896] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103898] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103900] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103902] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103904] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103906] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103907] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103909] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103911] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan  8 23:29:39 probook kernel: [   17.103913] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103916] cfg80211: World regulatory domain updated:
Jan  8 23:29:39 probook kernel: [   17.103917] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  8 23:29:39 probook kernel: [   17.103919] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103921] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103923] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103925] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.103927] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 23:29:39 probook kernel: [   17.354269] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0x5a0400
Jan  8 23:29:39 probook kernel: [   17.397782] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input13
Jan  8 23:29:39 probook kernel: [   18.682792] vesafb: mode is 1600x900x32, linelength=6400, pages=0
Jan  8 23:29:39 probook kernel: [   18.682795] vesafb: scrolling: redraw
Jan  8 23:29:39 probook kernel: [   18.682797] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jan  8 23:29:39 probook kernel: [   18.683951] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90012680000, using 5632k, total 5632k
Jan  8 23:29:39 probook kernel: [   18.684146] Console: switching to colour frame buffer device 200x56
Jan  8 23:29:39 probook kernel: [   18.684172] fb0: VESA VGA frame buffer device
Jan  8 23:29:39 probook kernel: [   45.956956] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: user_xattr
Jan  8 23:29:39 probook modem-manager[1059]: <info>  ModemManager (version 0.5) starting...
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Option
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Option High-Speed
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Samsung
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin AnyData
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin ZTE
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Wavecom
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Nokia
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Generic
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin SimTech
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin X22X
Jan  8 23:29:39 probook NetworkManager[1061]: <info> NetworkManager (version 0.9.1.90) is starting...
Jan  8 23:29:39 probook NetworkManager[1061]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jan  8 23:29:39 probook avahi-daemon[1063]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:39 probook avahi-daemon[1063]: Successfully dropped root privileges.
Jan  8 23:29:39 probook avahi-daemon[1063]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Linktop
Jan  8 23:29:39 probook NetworkManager[1061]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Sierra
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Longcheer
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Gobi
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Huawei
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Ericsson MBM
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin Novatel
Jan  8 23:29:39 probook modem-manager[1059]: <info>  Loaded plugin MotoC
Jan  8 23:29:39 probook avahi-daemon[1063]: Successfully called chroot().
Jan  8 23:29:39 probook avahi-daemon[1063]: Successfully dropped remaining capabilities.
Jan  8 23:29:39 probook dbus[1018]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan  8 23:29:39 probook avahi-daemon[1063]: Loading service file /services/udisks.service.
Jan  8 23:29:39 probook polkitd[1067]: started daemon version 0.102 using authority implementation `local' version `0.102'
Jan  8 23:29:39 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan  8 23:29:39 probook kernel: [   46.618023] type=1400 audit(1326050979.624:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1081 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.626163] type=1400 audit(1326050979.632:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1082 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.632575] type=1400 audit(1326050979.640:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1082 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.632784] type=1400 audit(1326050979.640:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1082 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.642878] type=1400 audit(1326050979.648:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1086 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.645440] ppdev: user-space parallel port driver
Jan  8 23:29:39 probook avahi-daemon[1063]: Failed to create server: Invalid domain name
Jan  8 23:29:39 probook avahi-daemon[1063]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:39 probook kernel: [   46.649298] init: avahi-daemon main process (1063) terminated with status 255
Jan  8 23:29:39 probook kernel: [   46.649320] init: avahi-daemon main process ended, respawning
Jan  8 23:29:39 probook avahi-daemon[1094]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:39 probook avahi-daemon[1094]: Successfully dropped root privileges.
Jan  8 23:29:39 probook avahi-daemon[1094]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:39 probook kernel: [   46.662365] type=1400 audit(1326050979.668:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1105 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.673508] type=1400 audit(1326050979.680:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1105 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.680096] type=1400 audit(1326050979.688:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1086 comm="apparmor_parser"
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: init!
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: update_system_hostname
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPluginIfupdown: management mode: unmanaged
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/wlan0, iface: wlan0)
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:45:00.0/net/eth0, iface: eth0)
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:45:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: end _init.
Jan  8 23:29:39 probook NetworkManager[1061]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  8 23:29:39 probook NetworkManager[1061]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  8 23:29:39 probook NetworkManager[1061]:    Ifupdown: get unmanaged devices count: 0
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: (36681520) ... get_connections.
Jan  8 23:29:39 probook NetworkManager[1061]:    SCPlugin-Ifupdown: (36681520) ... get_connections (managed=false): return empty list.
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile: parsing A3 ... 
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile:     read connection 'A3'
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile: parsing fire ... 
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile:     read connection 'fire'
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile: parsing GlobalCorpWLAN ... 
Jan  8 23:29:39 probook NetworkManager[1061]:    keyfile:     read connection 'GlobalCorpWLAN'
Jan  8 23:29:39 probook NetworkManager[1061]:    Ifupdown: get unmanaged devices count: 0
Jan  8 23:29:39 probook kernel: [   46.708600] type=1400 audit(1326050979.716:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1086 comm="apparmor_parser"
Jan  8 23:29:39 probook kernel: [   46.722753] type=1400 audit(1326050979.728:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1110 comm="apparmor_parser"
Jan  8 23:29:39 probook NetworkManager[1061]: <info> modem-manager is now available
Jan  8 23:29:39 probook NetworkManager[1061]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  8 23:29:39 probook NetworkManager[1061]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:44:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jan  8 23:29:39 probook NetworkManager[1061]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (driver hp-wmi)
Jan  8 23:29:39 probook NetworkManager[1061]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  8 23:29:39 probook NetworkManager[1061]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  8 23:29:39 probook NetworkManager[1061]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  8 23:29:39 probook NetworkManager[1061]: <info> Networking is enabled by state file
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): now managed
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  8 23:29:39 probook NetworkManager[1061]: <info> (wlan0): bringing up device.
Jan  8 23:29:39 probook avahi-daemon[1094]: Successfully called chroot().
Jan  8 23:29:39 probook avahi-daemon[1094]: Successfully dropped remaining capabilities.
Jan  8 23:29:39 probook avahi-daemon[1094]: Loading service file /services/udisks.service.
Jan  8 23:29:39 probook avahi-daemon[1094]: Failed to create server: Invalid domain name
Jan  8 23:29:39 probook avahi-daemon[1094]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:39 probook kernel: [   46.831439] init: avahi-daemon main process (1094) terminated with status 255
Jan  8 23:29:39 probook kernel: [   46.831461] init: avahi-daemon main process ended, respawning
Jan  8 23:29:39 probook avahi-daemon[1139]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:39 probook avahi-daemon[1139]: Successfully dropped root privileges.
Jan  8 23:29:39 probook avahi-daemon[1139]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:39 probook dbus[1018]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jan  8 23:29:39 probook anacron[1183]: Anacron 2.3 started on 2012-01-08
Jan  8 23:29:39 probook kernel: [   46.912523] init: failsafe main process (1025) killed by TERM signal
Jan  8 23:29:39 probook kernel: [   46.913755] init: apport pre-start process (1154) terminated with status 1
Jan  8 23:29:39 probook acpid: starting up with proc fs
Jan  8 23:29:39 probook acpid: 34 rules loaded
Jan  8 23:29:39 probook acpid: waiting for events: event logging is off
Jan  8 23:29:39 probook cron[1161]: (CRON) INFO (pidfile fd = 3)
Jan  8 23:29:39 probook kernel: [   46.936825] init: apport post-stop process (1191) terminated with status 1
Jan  8 23:29:39 probook cron[1194]: (CRON) STARTUP (fork ok)
Jan  8 23:29:39 probook cron[1194]: (CRON) INFO (Running @reboot jobs)
Jan  8 23:29:39 probook anacron[1183]: Normal exit (0 jobs run)
Jan  8 23:29:40 probook acpid: client connected from 1209[0:0]
Jan  8 23:29:40 probook acpid: 1 client rule loaded
Jan  8 23:29:40 probook avahi-daemon[1139]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1139]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1139]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1139]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1139]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.021712] init: avahi-daemon main process (1139) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.021734] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1216]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1216]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1216]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1216]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1216]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1216]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1216]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1216]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.093798] init: avahi-daemon main process (1216) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.093823] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1225]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1225]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1225]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan  8 23:29:40 probook avahi-daemon[1225]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1225]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1225]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1225]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1225]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.161081] init: avahi-daemon main process (1225) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.161106] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1231]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1231]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1231]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1231]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1231]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1231]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1231]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1231]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.189075] init: avahi-daemon main process (1231) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.189099] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1239]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1239]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1239]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1239]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1239]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1239]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1239]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1239]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.206560] init: avahi-daemon main process (1239) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.206584] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1245]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1245]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1245]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1245]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1245]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1245]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1245]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1245]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.227858] init: avahi-daemon main process (1245) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.227881] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1256]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1256]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1256]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook kernel: [   47.335612] [fglrx] Could not enable MSI; System prevented initialization
Jan  8 23:29:40 probook kernel: [   47.337278] [fglrx] Firegl kernel thread PID: 1259
Jan  8 23:29:40 probook kernel: [   47.338968] [fglrx] Firegl kernel thread PID: 1260
Jan  8 23:29:40 probook kernel: [   47.339984] [fglrx] Firegl kernel thread PID: 1261
Jan  8 23:29:40 probook kernel: [   47.340194] [fglrx] IRQ 10 Enabled
Jan  8 23:29:40 probook avahi-daemon[1256]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1256]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1256]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1256]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1256]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.345038] init: avahi-daemon main process (1256) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.345062] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1266]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1266]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1266]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1266]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1266]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1266]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1266]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1266]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.372825] init: avahi-daemon main process (1266) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.372851] init: avahi-daemon main process ended, respawning
Jan  8 23:29:40 probook avahi-daemon[1272]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jan  8 23:29:40 probook avahi-daemon[1272]: Successfully dropped root privileges.
Jan  8 23:29:40 probook avahi-daemon[1272]: avahi-daemon 0.6.30 starting up.
Jan  8 23:29:40 probook avahi-daemon[1272]: Successfully called chroot().
Jan  8 23:29:40 probook avahi-daemon[1272]: Successfully dropped remaining capabilities.
Jan  8 23:29:40 probook avahi-daemon[1272]: Loading service file /services/udisks.service.
Jan  8 23:29:40 probook avahi-daemon[1272]: Failed to create server: Invalid domain name
Jan  8 23:29:40 probook avahi-daemon[1272]: avahi-daemon 0.6.30 exiting.
Jan  8 23:29:40 probook kernel: [   47.398769] init: avahi-daemon main process (1272) terminated with status 255
Jan  8 23:29:40 probook kernel: [   47.398792] init: avahi-daemon respawning too fast, stopped
Jan  8 23:29:40 probook kernel: [   47.402873] vboxdrv: Found 1 processor cores.
Jan  8 23:29:40 probook kernel: [   47.411428] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jan  8 23:29:40 probook kernel: [   47.411431] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
Jan  8 23:29:40 probook kernel: [   47.429106] vboxpci: IOMMU not found (not registered)
Jan  8 23:29:40 probook bluetoothd[1307]: Bluetooth daemon 4.96
Jan  8 23:29:40 probook bluetoothd[1307]: Starting SDP server
Jan  8 23:29:40 probook bluetoothd[1307]: Listening for HCI events on hci0
Jan  8 23:29:40 probook kernel: [   47.462915] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan  8 23:29:40 probook kernel: [   47.462918] Bluetooth: BNEP filters: protocol multicast
Jan  8 23:29:40 probook kernel: [   47.467478] Bluetooth: RFCOMM TTY layer initialized
Jan  8 23:29:40 probook kernel: [   47.467481] Bluetooth: RFCOMM socket layer initialized
Jan  8 23:29:40 probook kernel: [   47.467483] Bluetooth: RFCOMM ver 1.11
Jan  8 23:29:40 probook kernel: [   47.523530] [fglrx] Gart USWC size:1280 M.
Jan  8 23:29:40 probook kernel: [   47.523534] [fglrx] Gart cacheable size:508 M.
Jan  8 23:29:40 probook kernel: [   47.523539] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jan  8 23:29:40 probook kernel: [   47.523541] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Jan  8 23:29:40 probook kernel: [   47.523543] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Jan  8 23:29:40 probook anacron[1392]: Anacron 2.3 started on 2012-01-08
Jan  8 23:29:40 probook anacron[1392]: Normal exit (0 jobs run)
Jan  8 23:29:40 probook bluetoothd[1307]: HCI dev 0 up
Jan  8 23:29:40 probook bluetoothd[1307]: Adapter /org/bluez/1307/hci0 has been enabled
Jan  8 23:29:40 probook kernel: [   47.789716] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Jan  8 23:29:40 probook kernel: [   47.793392] EXT4-fs (sda1): re-mounted. Opts: commit=0
Jan  8 23:29:41 probook kernel: [   47.985484] EXT4-fs (sda3): re-mounted. Opts: user_xattr,commit=0
Jan  8 23:29:41 probook dbus[1018]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan  8 23:29:41 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (wlan0): preparing device.
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): carrier is OFF
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): now managed
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): bringing up device.
Jan  8 23:29:41 probook kernel: [   48.699869] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 23:29:41 probook dbus[1018]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  8 23:29:41 probook kernel: [   48.754735] r8169 0000:45:00.0: eth0: link down
Jan  8 23:29:41 probook accounts-daemon[1422]: started daemon version 0.6.14
Jan  8 23:29:41 probook dbus[1018]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  8 23:29:41 probook kernel: [   48.784001] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): preparing device.
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan  8 23:29:41 probook NetworkManager[1061]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:45:00.0/net/eth0
Jan  8 23:29:41 probook NetworkManager[1061]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  8 23:29:41 probook NetworkManager[1061]: <info> wpa_supplicant started
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  8 23:29:41 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  8 23:29:41 probook dbus[1018]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jan  8 23:29:41 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jan  8 23:29:41 probook kernel: [   48.889741] init: plymouth-stop pre-start process (1526) terminated with status 1
Jan  8 23:29:42 probook dbus[1018]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan  8 23:29:42 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan  8 23:29:42 probook dbus[1018]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan  8 23:29:42 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jan  8 19:29:42 probook rtkit-daemon[1648]: Successfully called chroot.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Successfully dropped privileges.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Successfully limited resources.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Running.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Watchdog thread running.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Canary thread running.
Jan  8 23:29:42 probook anacron[1656]: Anacron 2.3 started on 2012-01-08
Jan  8 23:29:42 probook anacron[1656]: Normal exit (0 jobs run)
Jan  8 19:29:42 probook rtkit-daemon[1648]: Successfully made thread 1646 of process 1646 (n/a) owned by '104' high priority at nice level -11.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Supervising 1 threads of 1 processes of 1 users.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Successfully made thread 1662 of process 1646 (n/a) owned by '104' RT at priority 5.
Jan  8 19:29:42 probook rtkit-daemon[1648]: Supervising 2 threads of 1 processes of 1 users.
Jan  8 19:29:43 probook rtkit-daemon[1648]: Successfully made thread 1663 of process 1646 (n/a) owned by '104' RT at priority 5.
Jan  8 19:29:43 probook rtkit-daemon[1648]: Supervising 3 threads of 1 processes of 1 users.
Jan  8 19:29:43 probook rtkit-daemon[1648]: Successfully made thread 1664 of process 1646 (n/a) owned by '104' RT at priority 5.
Jan  8 19:29:43 probook rtkit-daemon[1648]: Supervising 4 threads of 1 processes of 1 users.
Jan  8 23:29:43 probook pulseaudio[1646]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jan  8 23:29:43  pulseaudio[1646]: last message repeated 2 times
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Auto-activating connection 'fire'.
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) starting connection 'fire'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 23:29:43 probook NetworkManager[1061]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0/wireless): connection 'fire' has security, and secrets exist.  No new secrets needed.
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: added 'ssid' value 'fire'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: added 'scan_ssid' value '1'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: added 'auth_alg' value 'OPEN'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: added 'psk' value '<omitted>'
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 23:29:43 probook NetworkManager[1061]: <info> Config: set interface ap_scan to 1
Jan  8 23:29:43 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan  8 23:29:43 probook kernel: [   50.752565] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Jan  8 23:29:43 probook kernel: [   50.843138] EXT4-fs (sda1): re-mounted. Opts: commit=0
Jan  8 23:29:44 probook kernel: [   51.037596] EXT4-fs (sda3): re-mounted. Opts: user_xattr,commit=0
Jan  8 23:29:44 probook wpa_supplicant[1426]: Trying to authenticate with 34:08:04:36:3b:79 (SSID='fire' freq=2462 MHz)
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  8 23:29:44 probook wpa_supplicant[1426]: Trying to associate with 34:08:04:36:3b:79 (SSID='fire' freq=2462 MHz)
Jan  8 23:29:44 probook kernel: [   51.833312] wlan0: authenticate with 34:08:04:36:3b:79 (try 1)
Jan  8 23:29:44 probook kernel: [   51.834848] wlan0: authenticated
Jan  8 23:29:44 probook kernel: [   51.835109] wlan0: associate with 34:08:04:36:3b:79 (try 1)
Jan  8 23:29:44 probook wpa_supplicant[1426]: Associated with 34:08:04:36:3b:79
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jan  8 23:29:44 probook kernel: [   51.837071] wlan0: RX AssocResp from 34:08:04:36:3b:79 (capab=0x411 status=0 aid=1)
Jan  8 23:29:44 probook kernel: [   51.837074] wlan0: associated
Jan  8 23:29:44 probook kernel: [   51.837978] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan  8 23:29:44 probook wpa_supplicant[1426]: WPA: Key negotiation completed with 34:08:04:36:3b:79 [PTK=CCMP GTK=TKIP]
Jan  8 23:29:44 probook wpa_supplicant[1426]: CTRL-EVENT-CONNECTED - Connection to 34:08:04:36:3b:79 completed (auth) [id=0 id_str=]
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'fire'.
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  8 23:29:44 probook NetworkManager[1061]: <info> dhclient started with pid 1689
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan  8 23:29:44 probook dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  8 23:29:44 probook dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jan  8 23:29:44 probook dhclient: All rights reserved.
Jan  8 23:29:44 probook dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  8 23:29:44 probook dhclient: 
Jan  8 23:29:44 probook dhclient: Listening on LPF/wlan0/e0:2a:82:e2:8f:86
Jan  8 23:29:44 probook dhclient: Sending on   LPF/wlan0/e0:2a:82:e2:8f:86
Jan  8 23:29:44 probook dhclient: Sending on   Socket/fallback
Jan  8 23:29:44 probook dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  8 23:29:44 probook dhclient: DHCPNAK from 192.168.0.1
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): DHCPv4 state changed preinit -> expire
Jan  8 23:29:44 probook dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): DHCPv4 state changed expire -> preinit
Jan  8 23:29:44 probook dhclient: DHCPOFFER of 192.168.0.101 from 192.168.0.1
Jan  8 23:29:44 probook dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
Jan  8 23:29:44 probook dhclient: DHCPACK of 192.168.0.101 from 192.168.0.1
Jan  8 23:29:44 probook dhclient: bound to 192.168.0.101 -- renewal in 2147483648 seconds.
Jan  8 23:29:44 probook NetworkManager[1061]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  8 23:29:44 probook NetworkManager[1061]: <info>   address 192.168.0.101
Jan  8 23:29:44 probook NetworkManager[1061]: <info>   prefix 24 (255.255.255.0)
Jan  8 23:29:44 probook NetworkManager[1061]: <info>   gateway 192.168.0.1
Jan  8 23:29:44 probook NetworkManager[1061]: <info>   nameserver '192.168.0.1'
Jan  8 23:29:44 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  8 23:29:45 probook NetworkManager[1061]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  8 23:29:45 probook NetworkManager[1061]: <info> Policy set 'fire' (wlan0) as default for IPv4 routing and DNS.
Jan  8 23:29:45 probook NetworkManager[1061]: <info> Activation (wlan0) successful, device activated.
Jan  8 23:29:45 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  8 23:29:45 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  8 23:29:45 probook dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  8 23:29:46 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  8 23:29:46 probook avahi: Avahi detected that your currently configured local DNS server serves
Jan  8 23:29:46 probook avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jan  8 23:29:46 probook avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jan  8 23:29:46 probook avahi: contact your administrator and convince him to use a different DNS domain,
Jan  8 23:29:46 probook avahi: since .local should be used exclusively for Zeroconf technology.
Jan  8 23:29:46 probook avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jan  8 23:29:48 probook kernel: [   55.437428] [UFW BLOCK] IN=wlan0 OUT= MAC=e0:2a:82:e2:8f:86:34:08:04:36:3b:79:08:00 SRC=199.47.217.147 DST=192.168.0.101 LEN=231 TOS=0x00 PREC=0x40 TTL=44 ID=7005 DF PROTO=TCP SPT=80 DPT=35823 WINDOW=305 RES=0x00 ACK PSH URGP=0 
Jan  8 19:29:48 probook rtkit-daemon[1648]: Successfully made thread 1873 of process 1873 (n/a) owned by '1000' high priority at nice level -11.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Supervising 5 threads of 2 processes of 2 users.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Successfully made thread 1874 of process 1873 (n/a) owned by '1000' RT at priority 5.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Supervising 6 threads of 2 processes of 2 users.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Successfully made thread 1875 of process 1873 (n/a) owned by '1000' RT at priority 5.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Supervising 7 threads of 2 processes of 2 users.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Successfully made thread 1876 of process 1873 (n/a) owned by '1000' RT at priority 5.
Jan  8 19:29:48 probook rtkit-daemon[1648]: Supervising 8 threads of 2 processes of 2 users.
Jan  8 23:29:48 probook pulseaudio[1873]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jan  8 23:29:51  pulseaudio[1873]: last message repeated 2 times
Jan  8 23:29:51 probook dbus[1018]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jan  8 23:29:51 probook dbus[1018]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jan  8 23:29:54 probook ntpdate[1755]: adjust time server 91.189.94.4 offset -0.111510 sec
Jan  8 23:29:55 probook kernel: [   62.415248] wlan0: no IPv6 routers present
Jan  8 23:30:01 probook kernel: [   68.344307] audit_printk_skb: 12 callbacks suppressed
Jan  8 23:30:01 probook kernel: [   68.344310] type=1400 audit(1326051001.361:19): apparmor="DENIED" operation="open" parent=2013 profile="/usr/lib/telepathy/telepathy-*" name="/usr/tmp/" pid=2014 comm="telepathy-haze" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jan  8 23:30:01 probook kernel: [   68.555368] [UFW BLOCK] IN=wlan0 OUT= MAC=e0:2a:82:e2:8f:86:34:08:04:36:3b:79:08:00 SRC=192.168.0.1 DST=192.168.0.101 LEN=379 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1044 DPT=44836 LEN=359 
Jan  8 23:30:04 probook NetworkManager[1061]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan  8 23:30:04 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan  8 23:30:04 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan  8 23:30:04 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  8 23:30:04 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  8 23:30:04 probook NetworkManager[1061]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Jan  8 23:30:08 probook dbus[1018]: [system] Failed to activate service 'org.freedesktop.Avahi': timed out
Jan  8 23:30:53 probook kernel: [  120.004148] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:34:08:04:36:3b:79:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=14090 PROTO=2 
Jan  8 23:30:55 probook dbus[1018]: [system] Failed to activate service 'org.freedesktop.Avahi': timed out
Jan  8 23:31:03 probook dbus[1018]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan  8 23:31:05 probook AptDaemon: INFO: Initializing daemon
Jan  8 23:31:05 probook dbus[1018]: [system] Successfully activated service 'org.debian.apt'
Jan  8 23:31:05 probook AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Jan  8 23:31:05 probook AptDaemon.Trans: INFO: Simulate was called
Jan  8 23:31:05 probook AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ef36a71d149e47bcbb1fb98fc8de13e0
Jan  8 23:31:17 probook AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Jan  8 23:32:06 probook bluetoothd[1307]: HCI dev 0 down
Jan  8 23:32:06 probook bluetoothd[1307]: Adapter /org/bluez/1307/hci0 has been disabled
Jan  8 23:32:50 probook dbus[1018]: [system] Failed to activate service 'org.freedesktop.Avahi': timed out
Jan  8 23:32:58 probook kernel: [  244.968084] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:34:08:04:36:3b:79:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=14091 PROTO=2 
Jan  8 23:35:02 probook kernel: [  369.930661] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:34:08:04:36:3b:79:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=14092 PROTO=2 
Jan  8 23:36:06 probook AptDaemon: INFO: Quitting due to inactivity
Jan  8 23:36:06 probook AptDaemon: INFO: Quitting was requested

```

```
f0y@probook:~$ cat /var/log/Xorg.0.log 
[    47.011] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    47.011] X Protocol Version 11, Revision 0
[    47.012] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    47.017] Current Operating System: Linux probook 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    47.017] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=4442b26e-50d9-4df2-8697-275ce772e651 ro quiet splash noapic nolapic acpi=force irqpoll pcie_aspm=off vt.handoff=7
[    47.017] Build Date: 19 October 2011  05:21:26AM
[    47.017] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    47.017] Current version of pixman: 0.22.2
[    47.017] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    47.017] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    47.017] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  8 23:29:40 2012
[    47.018] (==) Using config file: "/etc/X11/xorg.conf"
[    47.018] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    47.018] (==) ServerLayout "aticonfig Layout"
[    47.018] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    47.018] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    47.018] (**) |   |-->Device "aticonfig-Device[0]-0"
[    47.018] (==) Automatically adding devices
[    47.018] (==) Automatically enabling devices
[    47.018] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.018] 	Entry deleted from font path.
[    47.018] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.018] 	Entry deleted from font path.
[    47.018] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.018] 	Entry deleted from font path.
[    47.018] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.018] 	Entry deleted from font path.
[    47.018] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.018] 	Entry deleted from font path.
[    47.018] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    47.018] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    47.018] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    47.018] (II) Loader magic: 0x7e0220
[    47.018] (II) Module ABI versions:
[    47.018] 	X.Org ANSI C Emulation: 0.4
[    47.018] 	X.Org Video Driver: 10.0
[    47.018] 	X.Org XInput driver : 12.3
[    47.018] 	X.Org Server Extension : 5.0
[    47.019] (--) PCI:*(0:1:0:0) 1002:68e4:103c:1411 rev 0, Mem @ 0xc0000000/268435456, 0xd4500000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[    47.028] (II) Open ACPI successful (/var/run/acpid.socket)
[    47.028] (II) "extmod" will be loaded by default.
[    47.028] (II) "dbe" will be loaded by default.
[    47.028] (II) "glx" will be loaded by default.
[    47.028] (II) "record" will be loaded by default.
[    47.028] (II) "dri" will be loaded by default.
[    47.028] (II) "dri2" will be loaded by default.
[    47.028] (II) LoadModule: "extmod"
[    47.035] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    47.035] (II) Module extmod: vendor="X.Org Foundation"
[    47.035] 	compiled for 1.10.4, module version = 1.0.0
[    47.035] 	Module class: X.Org Server Extension
[    47.035] 	ABI class: X.Org Server Extension, version 5.0
[    47.035] (II) Loading extension MIT-SCREEN-SAVER
[    47.035] (II) Loading extension XFree86-VidModeExtension
[    47.035] (II) Loading extension XFree86-DGA
[    47.035] (II) Loading extension DPMS
[    47.035] (II) Loading extension XVideo
[    47.035] (II) Loading extension XVideo-MotionCompensation
[    47.035] (II) Loading extension X-Resource
[    47.035] (II) LoadModule: "dbe"
[    47.035] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    47.035] (II) Module dbe: vendor="X.Org Foundation"
[    47.035] 	compiled for 1.10.4, module version = 1.0.0
[    47.035] 	Module class: X.Org Server Extension
[    47.035] 	ABI class: X.Org Server Extension, version 5.0
[    47.035] (II) Loading extension DOUBLE-BUFFER
[    47.035] (II) LoadModule: "glx"
[    47.035] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    47.036] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    47.036] 	compiled for 6.9.0, module version = 1.0.0
[    47.036] (II) Loading extension GLX
[    47.036] (II) LoadModule: "record"
[    47.036] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    47.036] (II) Module record: vendor="X.Org Foundation"
[    47.036] 	compiled for 1.10.4, module version = 1.13.0
[    47.036] 	Module class: X.Org Server Extension
[    47.036] 	ABI class: X.Org Server Extension, version 5.0
[    47.036] (II) Loading extension RECORD
[    47.036] (II) LoadModule: "dri"
[    47.036] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    47.037] (II) Module dri: vendor="X.Org Foundation"
[    47.037] 	compiled for 1.10.4, module version = 1.0.0
[    47.037] 	ABI class: X.Org Server Extension, version 5.0
[    47.037] (II) Loading extension XFree86-DRI
[    47.037] (II) LoadModule: "dri2"
[    47.037] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    47.037] (II) Module dri2: vendor="X.Org Foundation"
[    47.037] 	compiled for 1.10.4, module version = 1.2.0
[    47.037] 	ABI class: X.Org Server Extension, version 5.0
[    47.037] (II) Loading extension DRI2
[    47.037] (II) LoadModule: "fglrx"
[    47.037] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    47.096] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    47.096] 	compiled for 1.4.99.906, module version = 8.88.7
[    47.096] 	Module class: X.Org Video Driver
[    47.096] (II) Loading sub module "fglrxdrm"
[    47.096] (II) LoadModule: "fglrxdrm"
[    47.096] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    47.096] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    47.096] 	compiled for 1.4.99.906, module version = 8.88.7
[    47.096] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[    47.096] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[    47.096] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:04:01
[    47.096] (++) using VT number 7

[    47.096] (WW) Falling back to old probe method for fglrx
[    47.104] (II) Loading PCS database from /etc/ati/amdpcsdb
[    47.104] (--) Chipset Supported AMD Graphics Processor (0x68E4) found
[    47.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    47.105] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    47.105] (II) AMD Video driver is signed
[    47.105] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    47.105] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    47.105] (II) fglrx(0): pEnt->device->identifier=0x20ae110
[    47.105] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    47.105] (II) Loading sub module "vgahw"
[    47.105] (II) LoadModule: "vgahw"
[    47.105] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    47.105] (II) Module vgahw: vendor="X.Org Foundation"
[    47.105] 	compiled for 1.10.4, module version = 0.1.0
[    47.105] 	ABI class: X.Org Video Driver, version 10.0
[    47.105] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    47.105] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    47.105] (==) fglrx(0): Default visual is TrueColor
[    47.105] (**) fglrx(0): Option "DPMS" "true"
[    47.105] (==) fglrx(0): RGB weight 888
[    47.105] (II) fglrx(0): Using 8 bits per RGB 
[    47.105] (==) fglrx(0): Buffer Tiling is ON
[    47.105] (II) Loading sub module "fglrxdrm"
[    47.105] (II) LoadModule: "fglrxdrm"
[    47.106] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    47.106] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    47.106] 	compiled for 1.4.99.906, module version = 8.88.7
[    47.128] ukiDynamicMajor: found major device number 249
[    47.128] ukiDynamicMajor: found major device number 249
[    47.128] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    47.128] ukiOpenDevice: node name is /dev/ati/card0
[    47.128] ukiOpenDevice: open result is 14, (OK)
[    47.128] ukiOpenByBusid: ukiOpenMinor returns 14
[    47.128] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    47.129] (==) fglrx(0): NoAccel = NO
[    47.129] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    47.129] (--) fglrx(0): Chipset: "AMD Radeon HD 6300M Series" (Chipset = 0x68e4)
[    47.129] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1411)
[    47.129] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    47.129] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    47.129] (--) fglrx(0): MMIO registers at 0xd4500000
[    47.129] (--) fglrx(0): I/O port at 0x00005000
[    47.129] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    47.130] (II) fglrx(0): AC Adapter is used
[    47.144] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    47.144] (II) Loading sub module "vbe"
[    47.144] (II) LoadModule: "vbe"
[    47.145] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    47.145] (II) Module vbe: vendor="X.Org Foundation"
[    47.145] 	compiled for 1.10.4, module version = 1.1.0
[    47.145] 	ABI class: X.Org Video Driver, version 10.0
[    47.145] (II) fglrx(0): VESA BIOS detected
[    47.145] (II) fglrx(0): VESA VBE Version 3.0
[    47.145] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    47.145] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    47.145] (II) fglrx(0): VESA VBE OEM Software Rev: 12.20
[    47.145] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    47.145] (II) fglrx(0): VESA VBE OEM Product: PARK
[    47.145] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    47.239] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    47.239] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    47.239] (II) fglrx(0): PCIE card detected
[    47.239] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    47.239] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    47.246] (II) fglrx(0): Using adapter: 1:0.0.
[    47.292] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    47.364] (II) fglrx(0): Interrupt handler installed at IRQ 10.
[    47.364] (II) fglrx(0): RandR 1.2 support is enabled!
[    47.364] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    47.364] (==) fglrx(0): Center Mode is disabled 
[    47.364] (II) Loading sub module "fb"
[    47.364] (II) LoadModule: "fb"
[    47.365] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.365] (II) Module fb: vendor="X.Org Foundation"
[    47.365] 	compiled for 1.10.4, module version = 1.0.0
[    47.365] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    47.365] (II) Loading sub module "ddc"
[    47.365] (II) LoadModule: "ddc"
[    47.365] (II) Module "ddc" already built-in
[    47.531] (II) fglrx(0): Finished Initialize PPLIB!
[    47.531] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    47.531] (II) fglrx(0): Output DFP1 has no monitor section
[    47.531] (II) fglrx(0): Output CRT1 has no monitor section
[    47.531] (II) Loading sub module "ddc"
[    47.531] (II) LoadModule: "ddc"
[    47.531] (II) Module "ddc" already built-in
[    47.531] (II) fglrx(0): Connected Display0: LVDS
[    47.531] (II) fglrx(0): Display0 EDID data ---------------------------
[    47.531] (II) fglrx(0): Manufacturer: AUO  Model: 129e  Serial#: 0
[    47.531] (II) fglrx(0): Year: 2009  Week: 1
[    47.531] (II) fglrx(0): EDID Version: 1.3
[    47.531] (II) fglrx(0): Digital Display Input
[    47.531] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    47.531] (II) fglrx(0): Gamma: 2.20
[    47.531] (II) fglrx(0): No DPMS capabilities specified
[    47.531] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    47.531] (II) fglrx(0): First detailed timing is preferred mode
[    47.531] (II) fglrx(0): redX: 0.620 redY: 0.340   greenX: 0.325 greenY: 0.570
[    47.532] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    47.532] (II) fglrx(0): Manufacturer's mask: 0
[    47.532] (II) fglrx(0): Supported detailed timing:
[    47.532] (II) fglrx(0): clock: 107.8 MHz   Image Size:  382 x 214 mm
[    47.532] (II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1966 h_border: 0
[    47.532] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[    47.532] (II) fglrx(0): Unknown vendor-specific block f
[    47.532] (II) fglrx(0):  AUO
[    47.532] (II) fglrx(0):  B173RW01 V2
[    47.532] (II) fglrx(0): EDID (in hex):
[    47.532] (II) fglrx(0): 	00ffffffffffff0006af9e1200000000
[    47.532] (II) fglrx(0): 	01130103802615780ac4959e57539226
[    47.532] (II) fglrx(0): 	0f505400000001010101010101010101
[    47.532] (II) fglrx(0): 	0101010101011c2a406e61840c303020
[    47.532] (II) fglrx(0): 	36007ed6100000180000000f00000000
[    47.532] (II) fglrx(0): 	00000000000000000020000000fe0041
[    47.532] (II) fglrx(0): 	554f0a202020202020202020000000fe
[    47.532] (II) fglrx(0): 	004231373352573031205632200a0026
[    47.532] (II) fglrx(0): End of Display0 EDID data --------------------
[    47.542] (II) fglrx(0): EDID for output LVDS
[    47.542] (II) fglrx(0): Manufacturer: AUO  Model: 129e  Serial#: 0
[    47.542] (II) fglrx(0): Year: 2009  Week: 1
[    47.542] (II) fglrx(0): EDID Version: 1.3
[    47.542] (II) fglrx(0): Digital Display Input
[    47.542] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    47.542] (II) fglrx(0): Gamma: 2.20
[    47.542] (II) fglrx(0): No DPMS capabilities specified
[    47.542] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    47.542] (II) fglrx(0): First detailed timing is preferred mode
[    47.542] (II) fglrx(0): redX: 0.620 redY: 0.340   greenX: 0.325 greenY: 0.570
[    47.542] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    47.542] (II) fglrx(0): Manufacturer's mask: 0
[    47.542] (II) fglrx(0): Supported detailed timing:
[    47.542] (II) fglrx(0): clock: 107.8 MHz   Image Size:  382 x 214 mm
[    47.542] (II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1966 h_border: 0
[    47.542] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[    47.542] (II) fglrx(0): Unknown vendor-specific block f
[    47.542] (II) fglrx(0):  AUO
[    47.542] (II) fglrx(0):  B173RW01 V2
[    47.542] (II) fglrx(0): EDID (in hex):
[    47.542] (II) fglrx(0): 	00ffffffffffff0006af9e1200000000
[    47.542] (II) fglrx(0): 	01130103802615780ac4959e57539226
[    47.542] (II) fglrx(0): 	0f505400000001010101010101010101
[    47.542] (II) fglrx(0): 	0101010101011c2a406e61840c303020
[    47.542] (II) fglrx(0): 	36007ed6100000180000000f00000000
[    47.542] (II) fglrx(0): 	00000000000000000020000000fe0041
[    47.542] (II) fglrx(0): 	554f0a202020202020202020000000fe
[    47.542] (II) fglrx(0): 	004231373352573031205632200a0026
[    47.542] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    47.542] (II) fglrx(0): Printing DDC gathered Modelines:
[    47.542] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Printing probed modes for output LVDS
[    47.542] (II) fglrx(0): Modeline "1600x900"x60.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "1440x900"x60.0  107.80  1440 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "1280x768"x60.0  107.80  1280 1648 1680 1966  768 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "1280x720"x60.0  107.80  1280 1648 1680 1966  720 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "1024x768"x60.0  107.80  1024 1648 1680 1966  768 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "1024x600"x60.0  107.80  1024 1648 1680 1966  600 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "800x600"x60.0  107.80  800 1648 1680 1966  600 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "800x480"x60.0  107.80  800 1648 1680 1966  480 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): Modeline "640x480"x60.0  107.80  640 1648 1680 1966  480 903 909 912 -hsync -vsync (54.8 kHz)
[    47.542] (II) fglrx(0): EDID for output DFP1
[    47.542] (II) fglrx(0): EDID for output CRT1
[    47.542] (II) fglrx(0): Output LVDS connected
[    47.542] (II) fglrx(0): Output DFP1 disconnected
[    47.542] (II) fglrx(0): Output CRT1 disconnected
[    47.542] (II) fglrx(0): Using exact sizes for initial modes
[    47.542] (II) fglrx(0): Output LVDS using initial mode 1600x900
[    47.542] (II) fglrx(0): Display dimensions: (380, 210) mm
[    47.542] (II) fglrx(0): DPI set to (106, 108)
[    47.542] (II) fglrx(0): Adapter AMD Radeon HD 6300M Series has 2 configurable heads and 1 displays connected.
[    47.543] (==) fglrx(0):  PseudoColor visuals disabled
[    47.543] (II) Loading sub module "ramdac"
[    47.543] (II) LoadModule: "ramdac"
[    47.543] (II) Module "ramdac" already built-in
[    47.543] (==) fglrx(0): NoDRI = NO
[    47.543] (==) fglrx(0): Capabilities: 0x00000000
[    47.543] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    47.543] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    47.543] (==) fglrx(0): UseFastTLS=0
[    47.543] (==) fglrx(0): BlockSignalsOnLock=1
[    47.543] (II) fglrx(0): Desktop Vsync is enabled.
[    47.543] (--) Depth 24 pixmap format is 32 bpp
[    47.543] (II) Loading extension ATIFGLRXDRI
[    47.543] (II) fglrx(0): doing swlDriScreenInit
[    47.543] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    47.543] ukiDynamicMajor: found major device number 249
[    47.543] ukiDynamicMajor: found major device number 249
[    47.543] ukiDynamicMajor: found major device number 249
[    47.543] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    47.543] ukiOpenDevice: node name is /dev/ati/card0
[    47.543] ukiOpenDevice: open result is 19, (OK)
[    47.543] ukiOpenByBusid: ukiOpenMinor returns 19
[    47.543] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    47.543] (II) fglrx(0): [uki] DRM interface version 1.0
[    47.543] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    47.543] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    47.543] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f066708d000
[    47.543] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    47.543] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    47.543] (II) fglrx(0): swlDriScreenInit done
[    47.543] (II) fglrx(0): Kernel Module Version Information:
[    47.543] (II) fglrx(0):     Name: fglrx
[    47.543] (II) fglrx(0):     Version: 8.88.7
[    47.543] (II) fglrx(0):     Date: Jul 28 2011
[    47.543] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    47.543] (II) fglrx(0): Kernel Module version matches driver.
[    47.543] (II) fglrx(0): Kernel Module Build Time Information:
[    47.543] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.0.0-14-generic
[    47.543] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    47.543] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    47.543] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    47.548] (II) fglrx(0): [uki] register handle = 0x00004000
[    47.578] (II) fglrx(0): DRI initialization successfull
[    47.578] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    47.578] (==) fglrx(0): Backing store disabled
[    47.578] (II) Loading extension FGLRXEXTENSION
[    47.578] (**) fglrx(0): DPMS enabled
[    47.578] (II) fglrx(0): Initialized in-driver Xinerama extension
[    47.578] (**) fglrx(0): Textured Video is enabled.
[    47.578] (II) LoadModule: "glesx"
[    47.578] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    47.583] (II) Module glesx: vendor="X.Org Foundation"
[    47.583] 	compiled for 1.4.99.906, module version = 1.0.0
[    47.583] (II) Loading extension GLESX
[    47.583] (II) fglrx(0): GLESX enableFlags = 592
[    47.583] (II) fglrx(0): GLESX is enabled
[    47.583] (II) LoadModule: "amdxmm"
[    47.583] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    47.583] (II) Module amdxmm: vendor="X.Org Foundation"
[    47.583] 	compiled for 1.4.99.906, module version = 2.0.0
[    47.593] (II) Loading extension AMDXVOPL
[    47.593] (II) Loading extension AMDXVBA
[    47.593] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[    47.594] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    47.595] (II) fglrx(0): Enable composite support successfully
[    47.595] (WW) fglrx(0): Option "VendorName" is not used
[    47.595] (WW) fglrx(0): Option "ModelName" is not used
[    47.595] (II) fglrx(0): X context handle = 0x1
[    47.595] (II) fglrx(0): [DRI] installation complete
[    47.600] (==) fglrx(0): Silken mouse enabled
[    47.600] (==) fglrx(0): Using HW cursor of display infrastructure!
[    47.600] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    47.600] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    47.600] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    48.536] (--) RandR disabled
[    48.536] (II) Initializing built-in extension Generic Event Extension
[    48.536] (II) Initializing built-in extension SHAPE
[    48.536] (II) Initializing built-in extension MIT-SHM
[    48.536] (II) Initializing built-in extension XInputExtension
[    48.536] (II) Initializing built-in extension XTEST
[    48.536] (II) Initializing built-in extension BIG-REQUESTS
[    48.536] (II) Initializing built-in extension SYNC
[    48.536] (II) Initializing built-in extension XKEYBOARD
[    48.536] (II) Initializing built-in extension XC-MISC
[    48.536] (II) Initializing built-in extension SECURITY
[    48.536] (II) Initializing built-in extension XINERAMA
[    48.536] (II) Initializing built-in extension XFIXES
[    48.536] (II) Initializing built-in extension RENDER
[    48.536] (II) Initializing built-in extension RANDR
[    48.536] (II) Initializing built-in extension COMPOSITE
[    48.536] (II) Initializing built-in extension DAMAGE
[    48.536] (II) Initializing built-in extension GESTURE
[    48.537] ukiDynamicMajor: found major device number 249
[    48.537] ukiDynamicMajor: found major device number 249
[    48.537] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    48.537] ukiOpenDevice: node name is /dev/ati/card0
[    48.537] ukiOpenDevice: open result is 20, (OK)
[    48.537] ukiOpenByBusid: ukiOpenMinor returns 20
[    48.537] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    48.618] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    48.629] (II) fglrx(0): Enable the clock gating!
[    48.635] (II) fglrx(0): Desktop Vsync is enabled.
[    48.635] (II) fglrx(0): Setting screen physical size to 423 x 238
[    48.643] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.650] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    48.650] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.650] (II) LoadModule: "evdev"
[    48.651] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.651] (II) Module evdev: vendor="X.Org Foundation"
[    48.651] 	compiled for 1.10.2, module version = 2.6.0
[    48.651] 	Module class: X.Org XInput Driver
[    48.651] 	ABI class: X.Org XInput driver, version 12.3
[    48.651] (II) Using input driver 'evdev' for 'Power Button'
[    48.651] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.651] (**) Power Button: always reports core events
[    48.651] (**) Power Button: Device: "/dev/input/event2"
[    48.651] (--) Power Button: Found keys
[    48.651] (II) Power Button: Configuring as keyboard
[    48.651] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    48.651] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    48.651] (**) Option "xkb_rules" "evdev"
[    48.651] (**) Option "xkb_model" "pc105"
[    48.651] (**) Option "xkb_layout" "us"
[    48.653] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    48.653] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    48.653] (II) Using input driver 'evdev' for 'Video Bus'
[    48.653] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.653] (**) Video Bus: always reports core events
[    48.653] (**) Video Bus: Device: "/dev/input/event7"
[    48.653] (--) Video Bus: Found keys
[    48.653] (II) Video Bus: Configuring as keyboard
[    48.653] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:00/input/input6/event7"
[    48.653] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    48.653] (**) Option "xkb_rules" "evdev"
[    48.653] (**) Option "xkb_model" "pc105"
[    48.653] (**) Option "xkb_layout" "us"
[    48.655] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    48.655] (II) No input driver/identifier specified (ignoring)
[    48.655] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    48.655] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    48.655] (II) Using input driver 'evdev' for 'Sleep Button'
[    48.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.655] (**) Sleep Button: always reports core events
[    48.655] (**) Sleep Button: Device: "/dev/input/event0"
[    48.655] (--) Sleep Button: Found keys
[    48.655] (II) Sleep Button: Configuring as keyboard
[    48.655] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    48.655] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    48.655] (**) Option "xkb_rules" "evdev"
[    48.655] (**) Option "xkb_model" "pc105"
[    48.655] (**) Option "xkb_layout" "us"
[    48.657] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event11)
[    48.657] (II) No input driver/identifier specified (ignoring)
[    48.657] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    48.657] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    48.657] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    48.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.657] (**) Logitech USB Receiver: always reports core events
[    48.657] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    48.658] (--) Logitech USB Receiver: Found keys
[    48.658] (II) Logitech USB Receiver: Configuring as keyboard
[    48.658] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input4/event4"
[    48.658] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    48.658] (**) Option "xkb_rules" "evdev"
[    48.658] (**) Option "xkb_model" "pc105"
[    48.658] (**) Option "xkb_layout" "us"
[    48.658] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    48.658] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    48.658] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    48.658] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    48.658] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.658] (**) Logitech USB Receiver: always reports core events
[    48.658] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    48.658] (--) Logitech USB Receiver: Found 20 mouse buttons
[    48.658] (--) Logitech USB Receiver: Found scroll wheel(s)
[    48.658] (--) Logitech USB Receiver: Found relative axes
[    48.658] (--) Logitech USB Receiver: Found x and y relative axes
[    48.658] (--) Logitech USB Receiver: Found absolute axes
[    48.658] (II) evdev-grail: failed to open grail, no gesture support
[    48.658] (--) Logitech USB Receiver: Found keys
[    48.658] (II) Logitech USB Receiver: Configuring as mouse
[    48.658] (II) Logitech USB Receiver: Configuring as keyboard
[    48.658] (II) Logitech USB Receiver: Adding scrollwheel support
[    48.658] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    48.658] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.658] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input5/event5"
[    48.658] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    48.658] (**) Option "xkb_rules" "evdev"
[    48.658] (**) Option "xkb_model" "pc105"
[    48.658] (**) Option "xkb_layout" "us"
[    48.658] (II) Logitech USB Receiver: initialized for relative axes.
[    48.658] (WW) Logitech USB Receiver: ignoring absolute axes.
[    48.659] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    48.659] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    48.659] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    48.659] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    48.659] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    48.659] (II) No input driver/identifier specified (ignoring)
[    48.659] (II) config/udev: Adding input device HP Webcam [2 MP Fixed] (/dev/input/event10)
[    48.659] (**) HP Webcam [2 MP Fixed]: Applying InputClass "evdev keyboard catchall"
[    48.659] (II) Using input driver 'evdev' for 'HP Webcam [2 MP Fixed]'
[    48.659] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.659] (**) HP Webcam [2 MP Fixed]: always reports core events
[    48.659] (**) HP Webcam [2 MP Fixed]: Device: "/dev/input/event10"
[    48.659] (--) HP Webcam [2 MP Fixed]: Found keys
[    48.659] (II) HP Webcam [2 MP Fixed]: Configuring as keyboard
[    48.659] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input10/event10"
[    48.659] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Fixed]" (type: KEYBOARD)
[    48.659] (**) Option "xkb_rules" "evdev"
[    48.659] (**) Option "xkb_model" "pc105"
[    48.660] (**) Option "xkb_layout" "us"
[    48.660] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event8)
[    48.660] (II) No input driver/identifier specified (ignoring)
[    48.660] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event9)
[    48.660] (II) No input driver/identifier specified (ignoring)
[    48.664] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    48.664] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    48.664] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    48.664] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.664] (**) AT Translated Set 2 keyboard: always reports core events
[    48.664] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    48.664] (--) AT Translated Set 2 keyboard: Found keys
[    48.665] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    48.665] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    48.665] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    48.665] (**) Option "xkb_rules" "evdev"
[    48.665] (**) Option "xkb_model" "pc105"
[    48.665] (**) Option "xkb_layout" "us"
[    48.665] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[    48.665] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    48.665] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    48.665] (II) LoadModule: "synaptics"
[    48.665] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    48.665] (II) Module synaptics: vendor="X.Org Foundation"
[    48.665] 	compiled for 1.10.4, module version = 1.4.1
[    48.665] 	Module class: X.Org XInput Driver
[    48.665] 	ABI class: X.Org XInput driver, version 12.3
[    48.665] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    48.665] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    48.665] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    48.665] (**) Option "Device" "/dev/input/event13"
[    48.665] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5686
[    48.665] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4548
[    48.665] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    48.665] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    48.665] (--) SynPS/2 Synaptics TouchPad: buttons: left double triple
[    48.665] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.665] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    48.665] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input13/event13"
[    48.666] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    48.666] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    48.666] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    48.666] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    48.666] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    48.666] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    48.666] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    48.666] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    48.666] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.666] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    48.666] (II) No input driver/identifier specified (ignoring)
[    48.667] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    48.667] (II) No input driver/identifier specified (ignoring)
[    48.667] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    48.667] (II) No input driver/identifier specified (ignoring)
[    48.671] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event12)
[    48.671] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    48.671] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    48.671] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.671] (**) HP WMI hotkeys: always reports core events
[    48.671] (**) HP WMI hotkeys: Device: "/dev/input/event12"
[    48.671] (--) HP WMI hotkeys: Found keys
[    48.671] (II) HP WMI hotkeys: Configuring as keyboard
[    48.671] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event12"
[    48.671] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    48.671] (**) Option "xkb_rules" "evdev"
[    48.671] (**) Option "xkb_model" "pc105"
[    48.671] (**) Option "xkb_layout" "us"
[    48.704] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    49.126] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    49.126] (II) fglrx(0): Printing DDC gathered Modelines:
[    49.126] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    50.256] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    50.860] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    50.860] (II) fglrx(0): Printing DDC gathered Modelines:
[    50.860] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    55.076] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    55.076] (II) fglrx(0): Printing DDC gathered Modelines:
[    55.076] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    55.525] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    55.525] (II) fglrx(0): Printing DDC gathered Modelines:
[    55.525] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)
[    55.545] (II) fglrx(0): EDID vendor "AUO", prod id 4766
[    55.545] (II) fglrx(0): Printing DDC gathered Modelines:
[    55.545] (II) fglrx(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1966  900 903 909 912 -hsync -vsync (54.8 kHz)

```

```
f0y@probook:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4500000-d45fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d4604000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at d4609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: d4400000-d44fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=43, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d0400000-d43fffff
	Prefetchable memory behind bridge: 00000000d4800000-00000000d49fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=44, subordinate=44, sec-latency=0
	Memory behind bridge: d0300000-d03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=45, subordinate=45, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0200000-d02fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at d4608000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=46, subordinate=46, sec-latency=32
	Memory behind bridge: d0100000-d01fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
	I/O ports at 6028 [size=8]
	I/O ports at 6034 [size=4]
	I/O ports at 6020 [size=8]
	I/O ports at 6030 [size=4]
	I/O ports at 6000 [size=32]
	Memory at d4607000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 VGA compatible controller: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d4500000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 5000 [size=256]
	Expansion ROM at d4540000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d4520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

44:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company Device 1453
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci

45:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1411
	Flags: bus master, fast devsel, latency 0, IRQ 5
	I/O ports at 2000 [size=256]
	Memory at d0004000 (64-bit, prefetchable) [size=4K]
	Memory at d0000000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at d0020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

```

---

### Post by f0y on 2012-01-09
Problem is solved. I turned off hand sensor of the mouse

---

### Post by svast on 2012-06-20
Hi f0y,

Glad to read you solved this issue.
Can you tell me how you turned off hand sensor ?

thanks a lot,
Stephane

---

