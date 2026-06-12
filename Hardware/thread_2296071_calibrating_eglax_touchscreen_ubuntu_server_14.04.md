---
title: "calibrating eglax touchscreen ubuntu server 14.04"
date: 2015-09-23
forum: Hardware
---

### Post by roma-i on 2015-09-23
Hi, people i am triying to set up a kiosk computer using a touch screen but i can not get it to work properly. I tried to configure it with xinput_calibrator but the result is a pointer in the top left corner no matter where i touch the screen.
So here is what i have done until now.
[LIST]
[*]1 I set up the kiosk computer folowing this guide [http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/) (no problem there)
[*]2 then i tried to configure the touch screen with xinput_calibrator and it generetes an unwanted result putting the cursor always in the top left corner. (I have this working on kubuntu 14.04)
[*]3 I started searching on the web and i found this guide [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen). That did not help me either becouse the the touch screen was not listed in the hardware section of the program.
[/LIST]
Ok here are some outputs:

```
#lsusb -v
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0eef D-WAV Scientific Co., Ltd
  idProduct          0x0001 eGalax TouchScreen
  bcdDevice            1.00
  iManufacturer           1 eGalax Inc.
  iProduct                2 USB TouchController
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB TouchScreen
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               5
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled


#xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius USB Optical Mouse                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController             id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Honeywell Imaging & Mobility     3310       id=10    [slave  keyboard (3)]
    &#8627; Chicony USB Keyboard                        id=12    [slave  keyboard (3)]
    &#8627; Chicony USB Keyboard                        id=13    [slave  keyboard (3)]


#xinput --list-props 14
Device 'eGalax Inc. USB TouchController':
    Device Enabled (131):    1
    Coordinate Transformation Matrix (133):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (260):    0
    Device Accel Constant Deceleration (261):    1.000000
    Device Accel Adaptive Deceleration (262):    1.000000
    Device Accel Velocity Scaling (263):    10.000000
    Device Product ID (250):    3823, 1
    Device Node (251):    "/dev/input/event8"
    Evdev Axis Inversion (264):    0, 0
    Evdev Axis Calibration (265):    <no items>
    Evdev Axes Swap (266):    0
    Axis Labels (267):    "Abs X" (281), "Abs Y" (282)
    Button Labels (268):    "Button Unknown" (253), "Button Unknown" (253), "Button Unknown" (253), "Button Wheel Up" (137), "Button Wheel Down" (138)
    Evdev Middle Button Emulation (269):    0
    Evdev Middle Button Timeout (270):    50
    Evdev Third Button Emulation (271):    0
    Evdev Third Button Emulation Timeout (272):    1000
    Evdev Third Button Emulation Button (273):    3
    Evdev Third Button Emulation Threshold (274):    20
    Evdev Wheel Emulation (275):    0
    Evdev Wheel Emulation Axes (276):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (277):    10
    Evdev Wheel Emulation Timeout (278):    200
    Evdev Wheel Emulation Button (279):    4
    Evdev Drag Lock Buttons (280):    0


#lsmod | grep usbtouch
usbtouchscreen         24576  0 


#lsusb | grep hid
i2c_hid                20480  0 
mac_hid                16384  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  3 i2c_hid,hid_generic,usbhid


#xinput_calibrator
Setting calibration data: 0, 2047, 0, 2047
Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=14
    current calibration values (from XInput): min_x=0, max_x=2047 and min_y=0, max_y=2047


Doing dynamic recalibration:
    Swapping X and Y axis...
    Setting calibration data: 570, 569, 1888, 1922
    --> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "eGalax Inc. USB TouchController"
    Option    "Calibration"    "570 569 1888 1922"
    Option    "SwapAxes"    "1"
EndSection

```
I really have not clue of what can i do to fix this so please I apreciate any help

---

