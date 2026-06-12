---
title: "INTREPID and Logitech MX1000"
date: 2008-10-31
forum: Hardware
---

### Post by pototo on 2008-10-31
Hi, I've been using ubuntu for two years, with a Logitech MX1000 mouse, and i've not had any problems with it, but now I've installed INTREPID and the mouse has some annoying behavior. 

The fact is that when I use the wheel to scroll down, the scroll randomly jumps to the beginning of the page, which make scroll almost unusable. Like I said, I've never had this behavior using EDGY, FEISTY, GUTSY or HARDY.

I've made some changes to xorg.conf, but no matter what I try, the problem remains the same. Now I'm using this:

```

Section "InputDevice"
    Identifier    "MX1000"
    Driver            "evdev"
    Option        "CorePointer"
    Option        "Protocol"    "ImPS/2"
    Option        "Dev Name"    "Logitech USB Receiver"
#    Option        "Dev Phys"    "usb-0000:00:02.0-4/input1"
    Option        "Device"    "/dev/input/mx1000"
    Option        "HWheelRelativeAxisButtons"    "7 6"

#    Option        "Device"    "/dev/input/by-id/usb-Logitech_USB_Receiver-mouse"
#    Option        "Buttons"    "12"
#    Option        "ZAxisMapping"    "4 5"
#    Option            "SendCoreEvents" "true"
#    Option        "ButtonMapping"    "1 2 3 4 5 8 9 10 11 12"
#    Option        "HWCursor"    "off"
EndSection

```Also tried:
```
Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection
```with no success.

This is my cat /proc/bus/input/devices:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c504 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c504 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.1/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=20017
B: KEY=1fffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 2000000 1878 d800d000 1e0000 0 0 0
B: REL=30f
B: MSC=10
B: LED=ff00

I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-6/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.0/input/input3
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=20017
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

```As you may see, I'm using two "Logitech USB Receiver". One is for the keyboard, and a mouse that I'm not using, and the second is for MX1000. I've tried unplugging the wireless keyboard and attaching a wired one, but it makes no difference.

This is my Xorg.0.log:```

(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "CorePointer"
(**) MX1000: always reports core events
(**) MX1000: Device: "/dev/input/mx1000"
(II) MX1000: Found x and y relative axes
(II) MX1000: Found 16 mouse buttons
(II) MX1000: Configuring as mouse
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (MX1000)
(II) XINPUT: Adding extended input device "MX1000" (type: MOUSE)
(**) MX1000: YAxisMapping: buttons 4 and 5
(**) MX1000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Macintosh mouse button emulation
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech USB Receiver
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech USB Receiver
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech USB Receiver
(EE) config/hal: NewInputDeviceRequest failed
```

I've had some success using the driver "mouse", protocol "ImPS/2" and Option "AutoAddDevices" "false". This corrects the wheel behavior, but makes impossible to use more than 3 buttons.

Maybe I have to downgrade evdev (I don't know how to do it) or deactivate hal, any ideas? I think this is an Xorg related bug, but I'm not sure.

---

### Post by Oleq on 2008-10-31
I've been using that code in 8.04 and everything worked well. In 8.10 I've got the same problem though :(
```
Section "InputDevice"
        Identifier      "Configured Mouse"

        Driver          "evdev"
        Option          "Name"              "Logitech USB Optical Mouse"
        Option          "Phys"          "usb-*/input0"
        Option          "Device"                "/dev/input/event2"
        Option          "Resolution"            "1000"
        Option          "Emulate3Buttons"       "no"
        Option          "RelHWHEELMapTo" "Buttons 6 7"
EndSection
```

---

### Post by pototo on 2008-10-31
Maybe it has something to do with new evdev driver in Intrepid (xserver-xorg-input-evdev_2.0.99+git20080912). Maybe downgrading to previous version could be a solution, but I don't know how to do it, or if it is even possible without downgrading xorg.

---

### Post by totaldrk62 on 2008-10-31
I think mice are being handled by HAL now which basically tells your xorg.conf file to piss off. At least with mice. I'm using a Logitech MX700 and my back and forward buttons aren't working in my window manager any more. When I checked my xorg my mouse had actually been commented out by the update manager. It still works in Firefox fine but not in metacity which I can't figure out.

---

### Post by pototo on 2008-10-31
> **totaldrk62 said:**
> I think mice are being handled by HAL now which basically tells your xorg.conf file to piss off. At least with mice. I'm using a Logitech MX700 and my back and forward buttons aren't working in my window manager any more. When I checked my xorg my mouse had actually been commented out by the update manager. It still works in Firefox fine but not in metacity which I can't figure out.

And is there any workaround to prevent HAL handling mice?

---

### Post by pototo on 2008-10-31
With this xorg.conf mouse scroll issues dissapear, but it turns into a 5-button one, so it's useless since I need side-wheel buttons.
```
Section "InputDevice"
    Identifier     "MX1000"
    Driver         "mouse" 
    Option         "CorePointer"
    Option         "Device"     "/dev/input/mice" 
    Option         "Protocol"     "ImPS/2" 
    Option         "ZAxisMapping"     "4 5" 
    Option         "Emulate3Buttons" "true" 
    Option         "ButtonMapping" "1 2 3 6 7 8 9 10 11 12 13 14" 
EndSection

Section "ServerFlags"
    Option         "AutoAddDevices"    "false"
EndSection
```from Intrepid release notes:> 
X.Org Input Devices.
The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 
It seems that you can edit keyboard settings, but it says nothing about mouse settings.

---

### Post by teaker1s on 2008-10-31
out of interest has anyone tried this project
[http://www.hidpoint.com/]("http://http://www.hidpoint.com/")

---

### Post by pototo on 2008-10-31
> **teaker1s said:**
> out of interest has anyone tried this project
[http://www.hidpoint.com/]("http://http://www.hidpoint.com/")

Would try, but there's no support for Intrepid, only for 2.6.24 kernel.

---

### Post by teaker1s on 2008-10-31
I'm fully aware of intrepid not supported-just wondering if anyone tried that project previously-if they update to newer kernels if it was previously any good could be a good solution

---

### Post by sunlander on 2008-10-31
Hi,

in Hardy i konfigured the middle mouse button of my MX1000 to "shut" a window/application. Now in Intrepid it dosent work anymore. Has anybody any idea to solve this problem?

Thank you guys and sorry for my bad english...

---

### Post by pototo on 2008-11-01
> **sunlander said:**
> Hi,

in Hardy i konfigured the middle mouse button of my MX1000 to "shut" a window/application. Now in Intrepid it dosent work anymore. Has anybody any idea to solve this problem?

Thank you guys and sorry for my bad english...

You may try xbindkeys to get your middle button to do this. Use xev to know wich button number is middle button of your mouse.

---

### Post by sunlander on 2008-11-01
That was my first thought, too (it worked this way in Hardy...). Unfortunately, Inteprid doesn't seem to support xautomation. xbindkeys is still working, although the config file has been re-named to ".xbindkeys" instead of ".xbindkeysrc".

I'm really looking forward to your answers!

---

### Post by pototo on 2008-11-01
> **sunlander said:**
> That was my first thought, too (it worked this way in Hardy...). Unfortunately, Inteprid doesn't seem to support xautomation. xbindkeys is still working, although the config file has been re-named to ".xbindkeys" instead of ".xbindkeysrc".

I'm really looking forward to your answers!

I'm using xbindkeys right now with Intrepid, and the config file is still .xbindkeysrc. I don't know if xautomation is still working because I use xmacro instead. Take a look at this:

[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

---

### Post by xpd259 on 2009-03-08
has any one had any joy with this??
my mx1000 mouse also does the scrolling dance 
and needs unplugging and re-pluging in when i boot up to get it to work some times

---

### Post by xpd259 on 2009-03-08
has anybody had any joy with this? 
i really don't want to get a new mouse to but I really can't stand the 
random scrolling between top and bottom of pages and desktops

---

