---
title: "Logitech MX600 mouse volume buttons don't work"
date: 2010-08-03
forum: Hardware
---

### Post by Aakkosti on 2010-08-03
I have a Logitech MX600 mouse that came in S530 keyboard + mouse bundle. The bundle is Mac themed but I believe the mouse is just a white variant of the standard MX600. The keyboard works well in Ubuntu 10.4 but the mouse's volume up/down buttons aren't recognized. Xev recognizes buttons 1-10: standard buttons, side buttons, the four-way mouse wheel and the mute button but I can't make the mute button do anything useful.

I tried following the instructions in [https://help.ubuntu.com/community/Logitech_MX610](https://help.ubuntu.com/community/Logitech_MX610) but there is no change in mouse behavior. [URL="https://help.ubuntu.com/community/Logitech_MX610"]
[/URL]
The computer in question is a standard PC desktop: I'm just using my keyboard-mouse combo I used with my Mac.

Here's my unmodified xorg.conf:

```
Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
EndSection

```and the result of "cat /proc/bus/input/devices"

```

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c214 Version=0110
N: Name="Logitech Logitech Attack 3"
P: Phys=usb-0000:00:12.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input3
U: Uniq=
H: Handlers=event3 js0 
B: EV=1b
B: KEY=7ff00000000 0 0 0 0
B: ABS=7
B: MSC=10

I: Bus=0003 Vendor=046d Product=c50c Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50c Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
U: Uniq=
H: Handlers=kbd mouse1 event5 
B: EV=1f
B: KEY=837fff042c332f bf08444400000000 ff0001 1f848a37cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

```(The Logitech Attack 3 is a joystick I have.)

---

### Post by maciej234 on 2010-08-03
can you edit the mouse under preferences>keyboard preferences?  Try adding a new button

---

### Post by Aakkosti on 2010-08-04
No, the only thing concerning mice there is the ability to use the numpad to move the mouse cursor.

I did some more digging. It appears that X configures the mouse correctly. From /var/log/Xorg.0.log:

```
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOA
RD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```I'm a bit confused at what that "Macintosh mouse button emulation" does. Quick googling doesn't reveal anything useful.

---

