---
title: "Problem with USB to VGA adaptor"
date: 2009-09-09
forum: Hardware
---

### Post by Alan Ward on 2009-09-09
Hi,

I am trying to connect a second screen to a Ubunto 9.04 based system.
I am using a USB to VGA adaptor - [USB2VGAE, by Startech]. 
I have tested the adaptor on a Windows system and it works fine.
I have read all the information I can find on the net, but I cannot get it to work.

There appear to be 2 'drivers' in the system:

/lib/xorg/modules/drivers/sisusb_drv.so

and 

/lib/modules/2.6.28-34-fitpc2/kernel/drivers/usb/misc/sisusbvga/sisusbvga.ko.

I don't understand the difference.

lsusb produces the following:

___________________________________________________________________
Bus 001 Device 005: ID 0711:5001 Magic Control Technology Corp. 
Bus 001 Device 004: ID 05dc:b035 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03eb:0002 Atmel Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
____________________________________________________________________

The first entry is the adaptor. If I expand that I get:
____________________________________________________________________
Bus 001 Device 005: ID 0711:5001 Magic Control Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0711 Magic Control Technology Corp.
  idProduct          0x5001 
  bcdDevice            0.01
  iManufacturer          16 MCT CORP 
  iProduct               32 USBVGA
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         48 MCT_Configuration
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface             64 MCT_Interface
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
        bEndpointAddress     0x03  EP 3 OUT
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
  bDeviceClass            0 (Defined at Interface level)(II) UnloadModule: "sisusb"
(II) Unloading /usr/lib/xorg/modules/drivers//sisusb_drv.so

  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
__________________________________________________________

I have added entries to my xorg.conf as advised by various forums I have come across:

___________________________________________________________
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen 0  "Screen0" 0 0
    Screen 1    "Screen1" RightOf "Screen0"  ###added by AGW
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "extmod"
    Load  "xtrap"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

### Added by AGW
Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    VertRefresh 50-75
     HorizSync 30-90
EndSection

Section "Device"
    Identifier "SIS"
    VendorName "StarTech"
    BoardName "USB2VGA"
    Driver "sisusb"
EndSection    

Section "Screen"
    Identifier "Screen1"
    Device "SIS"
    Monitor "Monitor1"
    DefaultDepth 16
    SubSection "Display"
        Depth 16
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
### End add


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ExaMem"                 # <i>
        #Option     "ExaScratch"             # <i>
        Option      "IgnoreACPI"             "true"
        Option      "NoPanel"                "true"
        #Option     "LidTimer"               # [<bool>]
        #Option     "NoFitting"              # [<bool>]
        #Option     "DownScale"              # [<bool>]
    Identifier  "Card0"
    Driver      "psb"
    VendorName  "Intel Corporation"
    BoardName   "System Controller Hub (SCH Poulsbo) Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection
________________________________________________________________

It is clear from the xorg log that the (first) driver above is being loaded, but the device is not found by the probe. I have included various sections from the log below:

_______________________________________________________________

(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep  8 16:37:05 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "SIS"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices

.
.
.
.

(II) LoadModule: "psb"
(II) Loading /usr/lib/xorg/modules/drivers//psb_drv.so
(II) Module psb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.29.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) Debug: psbSetup
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
(II) SISUSB: driver for SiSUSB chipsets: SIS315E/PRO USB
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for psb
(II) Debug: psbProbe
(--) Chipset Intel GMA500 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) PSB(0): Debug: Allocating new device
(WW) Falling back to old probe method for sisusb
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) PSB(0): Debug: psbPreInit
(II) PSB(0): psb_drv - 2.2.0.32L.0041

.
.
.
.

(II) UnloadModule: "sisusb"
(II) Unloading /usr/lib/xorg/modules/drivers//sisusb_drv.so

.
.
.

___________________________________________________________________

---

### Post by Sacha Von Brucke on 2011-03-13
Alan, 

I am having the same problem you had for using a STARTECH USB VGA DISPLAY ADAPTER, did you fiinally find any solution for it ?

Thank you by advance for your reply,


Sacha

---

### Post by Alan Ward on 2011-03-13
Hi, Sacha,

No. I gave up soon after that post. I had already spent too long trying to solve it.

Regards,
Alan

---

### Post by ironstorm on 2011-09-10
There **may** to be a distro that implements support for the MCT 0711:5110 chipset found in your device... see here about MAXI:  [http://ubuntuforums.org/showthread.php?p=11239619](http://ubuntuforums.org/showthread.php?p=11239619)

---

### Post by Peter Hite on 2013-02-15
I had the same problem.  Turns out you have to enable the usbvga dongle by using the following command before your start X:
modprobe sisusbvga

You should see the LED on the dongle turn on and your monitor sync with a red frame around it.  Starting X should work after that.

---

