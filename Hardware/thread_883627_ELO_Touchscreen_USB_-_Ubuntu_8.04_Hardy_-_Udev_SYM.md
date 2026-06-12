---
title: "ELO Touchscreen USB - Ubuntu 8.04 Hardy - Udev SYMLINK not working"
date: 2008-08-08
forum: Hardware
---

### Post by cybagorilla on 2008-08-08
Hi
I'm trying to install an Elo TouchSystems 2216 AccuTouch on an Ubuntu 8.04.
I picked many informations from several tutorials and forums to make a correct xorg.conf configuration. I connected the touchscreen with its USB interface, and i'm using the evtouch driver rather than elographics drivers that does not seems to work at all, nor the kernel module "elo" that does not works neither...

Here is my correct xorg.conf :

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

#Virtual Device "touchscreen" defined by udev rule in /etc/udec/rules.d
Section "InputDevice"
        Identifier      "touchscreen"
        Driver          "evtouch"
        Option          "device"        "/dev/input/event3"
#       Option          "device"        "/dev/input/touchscreen"
        Option          "MinX"          "550"
        Option          "MinY"          "700"
        Option          "MaxX"          "3400"
        Option          "MaxY"          "3350"
        Option          "MoveLimit"     "1"
        Option          "sendCoreEvents"        "On"
        Option          "SwapY" "On"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        InputDevice     "touchscreen"   "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

I took pretty time to set the MinX MaxX MinY MaxY options, by trying values and restarting gdm until i got a quite acceptable calibration, but now it works great.
It seems that the "movelimit" option is necesssary under Ubuntu 8.04, and i had to dig Xorg.conf man to discover the SwapY option :)

I only have 2 bugs left, that i'd like to fix :


1) I got a black screen EACH TIME i log off a gnome session. It seems to be a bug in the ati driver fglrx. I read somewhere that i had to choose between using the open driver with lesser graphics, or .. never login out :) i hope someone has a better solution ! I tried adding AlwaysRestartServer=true in gdm.conf-custom with no success, and setting sync settings in my xorg.conf screen settings ...with no success. Tell me if you have found something for this bug. Till i find something better, i just switch to console, then switch back to X with Ctrl+Alt+F1 then Alt+F7. Or sudo invoke-rc.d gdm restart when i feel brutal :p


2) The device selection of the touchscreen inputdevice section fails if i change usb connections... It's logical, the /dev/input/eventx depends of the order i plug usb devices ...

I tried to fix this with a udev rule. Here is the /proc/bus/input/device entry for my screen :

```
I: Bus=0003 Vendor=04e7 Product=0050 Version=0100
N: Name="EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch&#65533; USB Touchmonitor Interface"
P: Phys=usb-0000:00:0b.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3
U: Uniq=50U70445
H: Handlers=mouse1 event3 js0 
B: EV=1b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3
B: MSC=10
```

As there is a bad displayed character in the device name, i used its vender / product id to set my udev rule. Here is my /etc/udev/rules.d/10-touchscreen.rules :

```
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{IdVendor}=="04e7", ATTRS{IdProduct}=="0050", SYMLINK+="input/touchscreen"
```

Of course i corrected the xorg.conf with inverting the commented lines

```

#       Option          "device"        "/dev/input/event3"
        Option          "device"        "/dev/input/touchscreen"
```

It seems to be well seen by udev, but xorg fails to use the Symlink...
I have a pretty udev log :

```

UDEV  [1217603885.959244] add      /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3/js0 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3/js0
SUBSYSTEM=input
MAJOR=13
MINOR=0
SEQNUM=2685
UDEVD_EVENT=1
ID_VENDOR=EloTouchSystems,Inc
ID_MODEL=Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface
ID_REVISION=0100
ID_SERIAL=EloTouchSystems,Inc_Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface_50U70445
ID_SERIAL_SHORT=50U70445
ID_TYPE=hid
ID_BUS=usb
ID_CLASS=joystick
ID_PATH=pci-0000:00:0b.0-usb-0:4:1.0
DEVNAME=/dev/input/js0
DEVLINKS=/dev/input/by-id/usb-EloTouchSystems_Inc_Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface_50U70445-joystick /dev/input/by-path/pci-0000:00:0b.0-usb-0:4:1.0-joystick
```

And my Xorg.0.log :

```

(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (EVTouch TouchScreen)
(II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) Option "Device" "/dev/input/touchscreen"
(EE) xf86OpenSerial: Cannot open device /dev/input/touchscreen
        No such file or directory.
(WW) EVTouch TouchScreen: cannot open input device
couldn't enable device 4
SetClientVersion: 0 9
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
Receive 3D performance mode message with status: 00000001
```

Any suggestions ? i just don't understand why Xorg does not wants to use the device via Symlink whereas it's okay when setting the current /dev/intput/event ...

I hope i gave usefull informations, and thanks for helping !

---

### Post by theorifice on 2008-10-01
I have the same problem with an IRTouch K-15 touch screen.  When I configure X to use /dev/input/event#, the touchscreen works great.  I have to manually probe to find the event# though.  I made a udev rule to create a symlink /dev/input/irtouch but X won't use it.  I'm pretty sure it's because X is doing a scan of devices and it sees /dev/input/event# first and tries to configure that as a touch screen and when it comes time use the configuration file, that node is seen to be configured already.

Is there a way to have udev rename a node rather than create a symlink ?

---

### Post by jediko on 2008-12-11
[QUOTE=theorifice;5887271]I have the same problem with an IRTouch K-15 touch screen.  When I configure X to use /dev/input/event#, the touchscreen works great.  I have to manually probe to find the event# though. 



Hello

I'am trying to make work my irtouch screen but i can't

Did you use irtouch driver ?

---

### Post by magno32 on 2009-10-21
For what its worth, almost a year later.  I was having a similar issue with jaunty.  I haven't looked at Hardy with it, but jaunty creates a nice "by-id" section in /dev/input/ .  When I plug in the touchscreen, a symlink to it gets added to the by-id section.  Looks like this,

```
usb-EloTouchSystems_Inc_Elo_TouchSystems_2216_AccuTouch__USB_Touchmonitor_Interface_50U05994-event-joystick
```I'm posting this in hopes that it will help someone else.  Also, here is my final xorg.conf:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection
#Virtual Device "touchscreen" defined by udev rule in /etc/udec/rules.d
Section "InputDevice"
        Identifier      "touchscreen"
        Driver          "evtouch"
        Option          "device"        "/dev/input/by-id/usb-EloTouchSystems_Inc_Elo_TouchSystems_2216_AccuTouch__USB_Touchmonitor_Interface_50U05994-event-joystick"
#       Option          "device"        "/dev/input/touchscreen"
        Option          "MinX"          "530"
        Option          "MinY"          "670"
        Option          "MaxX"          "3470"
        Option          "MaxY"          "3400"
        Option          "MoveLimit"     "1"
        Option          "sendCoreEvents"        "On"
        Option          "SwapY" "On"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        InputDevice     "touchscreen"   "SendCoreEvents"
EndSection

```

---

