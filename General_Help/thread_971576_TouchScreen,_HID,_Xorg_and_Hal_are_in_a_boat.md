---
title: "TouchScreen, HID, Xorg and Hal are in a boat"
date: 2008-11-05
forum: General Help
---

### Post by nadras on 2008-11-05
Hello,

Just installed 8.10 with a touchscreen installed.
The touchscreen is recognized as a HID Device as shown in Xorg.log below.
**Is there a way to tell Xorg/Hal and all their friends NOT TO see and load the touchscreen as a HID device in order for me to freely access the touchscreen ?**

Thanks for any input !

-- Fab

Xorg.log excerpt: 
[I](II) config/hal: Adding input device HID TOUCH HID Touch Panel
(**) HID TOUCH HID Touch Panel: always reports core events
(**) HID TOUCH HID Touch Panel: Device: "/dev/input/event2"
(II) HID TOUCH HID Touch Panel: Found x and y absolute axes
(II) HID TOUCH HID Touch Panel: Found absolute touchpad
(II) HID TOUCH HID Touch Panel: Found 3 mouse buttons
(II) HID TOUCH HID Touch Panel: Configuring as mouse
(II) XINPUT: Adding extended input device "HID TOUCH HID Touch Panel" (type: MOUSE)
(**) HID TOUCH HID Touch Panel: YAxisMapping: buttons 4 and 5
(**) HID TOUCH HID Touch Panel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200[/I]

---

### Post by maxlem on 2009-01-09
I may mave the same touchscreen..

I got it in a MCE701 HTPC case. The touch screen was automatically detected in windoze. I get when I tap the screen, it clicks at the current mouse position. When I drag my finger, the cursor moves 1px... I think everything works, but that the calibration is wrong.

I have the Type A controller on this page

[http://www.mce701.com/viewtopic.php?f=1&t=3&sid=d08289dfe5e6b34b32c7654c18c53c5a](http://www.mce701.com/viewtopic.php?f=1&t=3&sid=d08289dfe5e6b34b32c7654c18c53c5a)

It comes with a .so modules that xorg refuses to load due to an xF86memset error.

what is thi xfhiddrv_drv.so driver?

I'm not even sur who makes the controller. lsusb gives 1234:8888 device ID.. probably semi-home made.

---

### Post by maxlem on 2009-01-12
I found a way to make it work

The calibration has to be done by hand, though

Here's the how-to

first get the mouse and event ID's :
```

cat /proc/bus/input/devices

```

mine was something like 

```

I: Bus=0003 Vendor=1234 Product=8888 Version=0100
N: Name="HID TOUCH HID Touch Panel"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input10
U: Uniq=
H: Handlers=mouse2 event3
B: EV=1b
B: KEY=30000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10

```

Then install the evtouch package :

```

sudo apt-get install xserver-xorg-input-evtouch

```

Then you have to modify your /etc/X11/xorg.conf and add :

```

Section "InputDevice"
    Identifier    "touchscreen"
    Driver    "evtouch"
    Option    "Mode" "Absolute" #not sure it is necessary
    Option    "Device"    "/dev/input/event3" #FIXME this can change during reboots, create symlink or link with /dev/input/by-id device's name
    Option    "DeviceName"    "touchscreen"
    Option    "MinX"        "0"
    Option    "MinY"        "0"
    Option    "MaxX"        "10000"
    Option    "MaxY"        "10000"
    Option    "ReportingMode"    "Raw"
    Option    "Emulate3Buttons"
    Option    "Emulate3Timeout"    "50"
    Option    "SendCoreEvents"
    Option    "MoveLimit" "10"
    #Option    "Calibrate"  "1"
    #Option    "Rotation" "cw"  
    #Option    "SwapX"    "1"
    #Option    "SwapY"    "1"
EndSection

```

Where you must set Min/Max values accordingly

you must also add this to Section ServerLayout:

```

  	InputDevice 	"touchscreen" "SendCoreEvents"

```


And that's it!

---

### Post by maxlem on 2009-01-15
create
```

sudo vim  /etc/udev/rules.d/10-local.rules

```

and add
```

SUBSYSTEM=="input", KERNEL=="event*", ATTRS{name}=="Touchkit HID-USB Touchscreen", SYMLINK+="input/touchscreen"

```

in xorg.conf, it becomes :

```

Section "InputDevice"
        Identifier  "touchscreen"
        Driver      "evtouch"
        Option      "Mode" "Absolute"
        Option      "Device" "/dev/input/touchscreen"
        Option      "DeviceName" "touchscreen"
        Option      "MinX" "0"
        Option      "MinY" "-9000"
        Option      "MaxX" "10700"
        Option      "MaxY" "9000"
        Option      "ReportingMode" "Raw"
        Option "TapTimer" "300" # default 200ms
        Option "LongTouchTimer" "500" # default 400ms
        Option "Emulate3Buttons" "false" # default true
        Option "Emulate3Timeout" "50" # default 50ms
        Option "MoveLimit" "30" # default 30 pixels
EndSection

```

---

