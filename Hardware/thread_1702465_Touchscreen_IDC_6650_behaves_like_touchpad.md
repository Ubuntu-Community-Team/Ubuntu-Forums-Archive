---
title: "Touchscreen: IDC 6650 behaves like touchpad"
date: 2011-03-07
forum: Hardware
---

### Post by jaxxed on 2011-03-07
Gateway zx all-in-one Desktop.

I have this machine running as my media machine, and things work (almost perfectly.)  The biggest problem for me is that my touchscreen acts really weird.
Movement and response is like a laptop touchpad, not like a tablet screen.

A quick check seems to me to show that the machine is trying to use the synaptics driver instead of the evtouch driver? I'm very unskilled in these matters.
I've checked the xorg.conf.d folder, but am unsure how to suggest to my machine that it would prefer the synaptics driver.

I've tried the base maverick, and all updates, and I've tried the natty-alpha-3.  I've also tried using the netbook-remix to see if it comes with any extra touchscreen aware items.

Here are some command outputs:

```

:~$ xinput  list --long 12
IDEACOM  IDC 6650                       	id=12	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 12
		Buttons supported: 12
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
		Button state:
		Class originated from: 12
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 0.000000 - 8191.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 12
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 0.000000 - 8191.000000
		  Resolution: 0 units/m
		  Mode: relative

```

Xorg.0.log:
```

[    39.821] (WW) Chicony 2.4G Multimedia Wireless Kit: ignoring absolute axes.
[    39.821] (II) config/udev: Adding input device Chicony 2.4G Multimedia Wireless Kit (/dev/input/mouse0)
[    39.821] (II) No input driver/identifier specified (ignoring)
[    39.822] (II) config/udev: Adding input device IDEACOM  IDC 6650 (/dev/input/event5)
[    39.822] (**) IDEACOM  IDC 6650: Applying InputClass "evdev touchpad catchall"
[    39.822] (**) IDEACOM  IDC 6650: Applying InputClass "touchpad catchall"
[    39.822] (II) LoadModule: "synaptics"
[    39.822] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    39.822] (II) Module synaptics: vendor="X.Org Foundation"
[    39.822]    compiled for 1.9.0, module version = 1.2.2
[    39.822]    Module class: X.Org XInput Driver
[    39.822]    ABI class: X.Org XInput driver, version 11.0
[    39.822] (II) Synaptics touchpad driver version 1.2.2
[    39.822] (**) Option "Device" "/dev/input/event5"
[    40.100] (II) IDEACOM  IDC 6650: x-axis range 0 - 8191
[    40.100] (II) IDEACOM  IDC 6650: y-axis range 0 - 8191
[    40.100] (II) IDEACOM  IDC 6650: pressure range 0 - 255
[    40.100] (II) IDEACOM  IDC 6650: finger width range 0 - 0
[    40.100] (II) IDEACOM  IDC 6650: buttons: left right
[    40.310] (--) IDEACOM  IDC 6650: touchpad found
[    40.310] (**) IDEACOM  IDC 6650: always reports core events
[    40.400] (II) XINPUT: Adding extended input device "IDEACOM  IDC 6650" (type: TOUCHPAD)
[    40.400] (**) IDEACOM  IDC 6650: (accel) keeping acceleration scheme 1
[    40.401] (**) IDEACOM  IDC 6650: (accel) acceleration profile 0
[    40.401] (**) IDEACOM  IDC 6650: (accel) acceleration factor: 2.000
[    40.401] (**) IDEACOM  IDC 6650: (accel) acceleration threshold: 4
[    40.560] (--) IDEACOM  IDC 6650: touchpad found
[    40.561] (II) config/udev: Adding input device IDEACOM  IDC 6650 (/dev/input/mouse1)
[    40.561] (II) No input driver/identifier specified (ignoring)

```


```

$> lsusb -v 
Bus 004 Device 003: ID 1cb6:6650
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x1cb6
  idProduct          0x6650
  bcdDevice            2.12
  iManufacturer           1 IDEACOM
  iProduct                2 IDC 6650
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     281
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
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by jaxxed on 2011-03-08
Every item in the forum that deals with this hardware, says that the screen works for them, out of the box, but that they have problems with calibration and event handling.

my xinput test, properly catches all sorts of events (I think correct events,) but I can't find any calibration tools (ev_calibrate won't execute,) and no interface for administering touch screens.

---

### Post by Favux on 2011-03-08
Hi jaxxed,

For calibration see if xinput_calibrator works for you:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

The thing to figure out is what driver to place it on, evdev or Synaptic.  Does it have more than two finger capabilities?

If so I'm not sure which driver is better.  Maybe evdev with ginn (gesture recognition).  That would probably be the way to go in Maverick but with Natty I don't know what the preference is yet.  I heard they were beefing up the Synaptic driver for gesture recognition.

Anyway the way to do it is to add a .conf file to the user custom location /etc/X11/xorg.conf.d and use a match line with IDEACOM IDC 6650 as a keyword, or some part of it anyway, to place it on the driver you want.  In Ubuntu the directory should already be there but if not just create it.  /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d so what's in it should control, but I'd number the .conf a little higher than the one with the driver in /usr/share/X11/xorg.conf.d just to be sure it runs last.  So if it was say 10-whatever.conf I'd make my custom one 12-whatever.conf.

---

### Post by jaxxed on 2011-03-08
So something like this:

Section "InputDevice"
    Identifier "IDEACOM IDC 6650"
    Driver "evtouch"
    MatchIsTouchscreen "on"
    MatchDevicePath "/dev/input/event*"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "IDEACOM IDC 6650"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "TapTimer" "200 ms"
    Option "LongTouchTimer" "400 ms"
EndSection


In something like /usr/share/99-idc.conf

I'll try it now.

---

### Post by jaxxed on 2011-03-08
I guess I probably don't need to double define the device path like that.  I'll try the wild card and then see if I can narrow the case down.  Also I'll avoid all of the options until after I try the different driver.

FYI:

$> ll /dev/input
mouse0
mouse1


those are probably my touchscreen and actual mouse?

---

### Post by Favux on 2011-03-08
That could be.

I think more something like this:
```
Section "InputDevice"
    Identifier "IDEACOM touchscreen class"
    MatchIsTouchscreen "on"
    MatchProduct "IDEACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "evtouch"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "TapTimer" "200 ms"
    Option "LongTouchTimer" "400 ms"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
EndSection
```
I'm guessing at the keyword from what you showed, I'd like to see the *xinput list*.  Driver after the matches.  You may not need the Touchscreen match.  Not sure you need all the Options like Reporting Mode.  Do you know if those coordinates apply to your screen?  SendCoreEvents stuff is deprecated starting with X server 1.7.

I doubt you need to use a number as high as 99.

---

### Post by jaxxed on 2011-03-09
I'll try your conf in the morning if I can get a chance. I'm inclined to agree at reducing the option list, I was just filling up the options from other pages that I saw.
I don't often look at xorg.conf files anymore, so I'm trying not to feel to old with 1.7

Thx for all the help so far.  If I can just get this working then I'll be really happy with this machine.

---

### Post by jaxxed on 2011-03-11
Any idea if there is a x64 deb for the calibrator about?

---

### Post by Favux on 2011-03-11
Nope, but as I recall compiling it was pretty straightforward.

---

### Post by jaxxed on 2011-03-11
I didn't put that other code into placee yet.  When I use the xinput_calibrator, I get the following:

media@media:~/src/xinput_calibrator-0.7.5/src$ ./xinput_calibrator 
Error: No calibratable devices found.

Is calibratable even a real word?  Just kidding.

I still haven't gotten your xorg.conf.d code to work yet, so I'll take a look at getting that in place first.  I'm assuming that xinput_cal needs to have an x-driver in place.

---

### Post by jaxxed on 2011-03-11
I get the same kind of behaviour with the evdev driver, but xorg still seems to think that it's found no driver.

the input calibrator still can't see any device

the more I play with it, the more I realize that the device is working, but it really is just a calibration issue.  I'll try a manual calibration in the xorg.conf.
The machine has the binary nvidia driver in place already, so all I have to do is add the input device.

```

media@media:~$ tail -n 18 /var/log/Xorg.0.log
[   843.152] (II) No input driver/identifier specified (ignoring)
[   843.153] (II) config/udev: Adding input device IDEACOM  IDC 6650 (/dev/input/event4)
[   843.153] (**) IDEACOM  IDC 6650: Applying InputClass "evdev touchpad catchall"
[   843.153] (**) IDEACOM  IDC 6650: Applying InputClass "touchpad catchall"
[   843.153] (**) IDEACOM  IDC 6650: always reports core events
[   843.153] (**) IDEACOM  IDC 6650: Device: "/dev/input/event4"
[   843.230] (II) IDEACOM  IDC 6650: Found 3 mouse buttons
[   843.230] (II) IDEACOM  IDC 6650: Found absolute axes
[   843.230] (II) evdev-grail: failed to open grail, no gesture support
[   843.230] (II) IDEACOM  IDC 6650: Found x and y absolute axes
[   843.230] (II) IDEACOM  IDC 6650: Found absolute touchpad.
[   843.230] (II) IDEACOM  IDC 6650: Configuring as touchpad
[   843.230] (**) IDEACOM  IDC 6650: YAxisMapping: buttons 4 and 5
[   843.230] (**) IDEACOM  IDC 6650: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   843.230] (II) XINPUT: Adding extended input device "IDEACOM  IDC 6650" (type: TOUCHPAD)
[   843.230] (II) IDEACOM  IDC 6650: initialized for absolute axes.
[   843.231] (II) config/udev: Adding input device IDEACOM  IDC 6650 (/dev/input/mouse1)
[   843.231] (II) No input driver/identifier specified (ignoring)

```

and as requested, the xinput
```

media@media:~$ xinput --list --long 12
IDEACOM  IDC 6650                       	id=12	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 12
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 12
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 4520.000000
		Class originated from: 12
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 3847.000000
		Class originated from: 12
		Detail for Valuator 2:
		  Label: Abs Z
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 12
		Detail for Valuator 3:
		  Label: Abs Rotary X
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 12
		Detail for Valuator 4:
		  Label: Abs Pressure
		  Range: 0.000000 - 255.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 12
		Detail for Valuator 5:
		  Label: None
		  Range: 0.000000 - 255.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000

```

---

### Post by jaxxed on 2011-03-11
I got things working out. I know have proper 'click where I touch' features. 

No i have to figure out an on-screen keyboard that doesn't crash the system (thanks gok), or load multiple instance (thanks gok,) or look fugly (thanks you know who,)

I'm normally a kde user, so I couldn't find the gesture controls to enable two-finger scrolling, so I have to find that.  Also I'm trying to figure out how to enlarge the panels and buttons, without having background-image fugliness.

Anyway thanks for you help.  Here are the final tips:

Installed driver xserver-xorg-input-evtouch

I created a file /usr/share/X11/xorg.conf.d/99.idc.conf:
```

Section "InputClass"
  Identifier "IDEACOM touchscreen class"
  MatchProduct "IDEACOM"
  MatchDevicePath "/dev/input/event*"
  Driver "evtouch"
  Option "MinX" "0"
  Option "MinY" "0"
  Option "MaxX" "8192"
  Option "MaxY" "8192"
EndSection

```

Changes to the initial plan were to create the definition as an input class, instead of an input device, and to drop some of the options.

When I ran the xinput_calibrater, it gave me results closer to -50/8192,-50/1049 - which produced an unusable screen.  The above configuration could still use some tweaking to get exact locations, but it works well.

If desired I will attache my xinput --list, but right now I'm on my other machine, as gok has taken access away during a system upgrade ... thanks gok.

J

---

### Post by Favux on 2011-03-12
Great!  Nice work.

To resize the panels you can use:
```
gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 42
```
The default is 24 and I think for the bottom panel its just bottom_panel_screen0.  You can check gconf editor.  I like 42, you may want something different.

---

### Post by jaxxed on 2011-03-12
natty drops support for xserver-xorg-input-evtouch due to lack of dependent xorg-input-abi-11.0 (natty uses abi 12).

I wuoldn't mind but Maverick doesn't handle the WIFI.  It thinks that the Chicony WIFI is an input device (I think) and doesn't let me see any networks.

I switched to evdev and synaptics, but can't get them to behave properly.

---

### Post by Favux on 2011-03-12
How many fingers does the IDEACOM support for touch?  If it's two or more fingers then you have to hope the kernel support for it is up to current MT (multitouch) specifications to use Synaptic.  The kernel driver is probably in the HID part.  Then it's a question of configuring the Synaptic driver correctly.  There are some settings the Maverick gui doesn't allow access to, but you can access them outside the gui.  I don't know about the Natty gui.

If it isn't MT specification compliant you'd have to stay in Maverick and figure out some sort of wifi work around.

---

### Post by jaxxed on 2011-03-14
The screen supports multi-touch in windows, and the xinput --test reports actions with the second and third finger (the fourth finger makes everything go silent.

I'm looking at utouch/grails, gpointer calibration, and toucheegg.

utouch doesn't seem to have any configuration panel, the gpointer calibration fails on launch and the toucheegg is pretty far 3rd party.

Any suggestions which to try?


Incidentally, I found a launchpad bug for the same issue: [https://bugs.launchpad.net/ubuntu/+bug/573006](https://bugs.launchpad.net/ubuntu/+bug/573006)

---

### Post by Favux on 2011-03-14
No, no real suggestions beyond using ginn if you could get evdev to work.

---

### Post by jaxxed on 2011-03-14
I'll try to go back to evdev, but I will only have the machine for a few more days.

I'll switch to a different model, which will likely have a different chipset.

In the meantime, I think that this thread could prove useful to others.  Thanks for doing good.

---

