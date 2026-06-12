---
title: "Touchpad/Trackpoint not working on Toshiba Portege z10t-a"
date: 2014-02-14
forum: Hardware
---

### Post by sbrookfield on 2014-02-14
I've just managed to install ubuntu on a new Toshiba Portege z10t-a

The touchscreen works, but the touchpad/trackpoint attached via a dock don't work

The dock is picked up by lsinput with the keyboard on event4 and joint mouse(touchpad/trackpoint on event 5 with the same usb device. The keyboard works, although it is missing some of the hotkeys

```
/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x930
   product : 0x807
   version : 273
   name    : "      USB Device"
   phys    : "usb-0000:00:1a.0-1.4.1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event5
   bustype : BUS_USB
   vendor  : 0x930
   product : 0x807
   version : 273
   name    : "      USB Device"
   phys    : "usb-0000:00:1a.0-1.4.1/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC


```

input-events when listening on event5 picks up signals when moving the trackpad

xinput detects it as a mouse (id13)

```
 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=9    [slave  pointer  (2)]
&#9116;   &#8627;       USB Device                            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - 3M                     id=10    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=15    [slave  keyboard (3)]
    &#8627;       USB Device                            id=12    [slave  keyboard (3)]

```

And xinput list-props 13 emits something reasonable...

```
Device '      USB Device':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (264):    0
    Device Accel Constant Deceleration (265):    1.000000
    Device Accel Adaptive Deceleration (266):    1.000000
    Device Accel Velocity Scaling (267):    10.000000
    Device Product ID (253):    2352, 2055
    Device Node (254):    "/dev/input/event5"
    Evdev Axis Inversion (268):    0, 0
    Evdev Axes Swap (270):    0
    Axis Labels (271):    "Rel X" (144), "Rel Y" (145), "Rel Z" (290), "Rel Rotary X" (291), "Rel Vert Wheel" (292), "Rel Misc" (293)
    Button Labels (272):    "Button Left" (137), "Button Middle" (138), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143), "Button Side" (285), "Button Extra" (286), "Button Forward" (287), "Button Back" (288), "Button Task" (289), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256)
    Evdev Middle Button Emulation (273):    0
    Evdev Middle Button Timeout (274):    50
    Evdev Third Button Emulation (275):    0
    Evdev Third Button Emulation Timeout (276):    1000
    Evdev Third Button Emulation Button (277):    3
    Evdev Third Button Emulation Threshold (278):    20
    Evdev Wheel Emulation (279):    0
    Evdev Wheel Emulation Axes (280):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (281):    10
    Evdev Wheel Emulation Timeout (282):    200
    Evdev Wheel Emulation Button (283):    4
    Evdev Drag Lock Buttons (284):    0


```

And it appears to be all enabled, but when I move it  the only thing it does is unhide / display the cursor - it does not move or click

Any ideas?

Thanks

---

### Post by luigi6 on 2014-03-10
Hi,
I see that this thread is three weeks old but I'm very interested in the status of ubuntu compatibility with Toshiba z10t.
So I was wondering, any progress made so far?
Also have you seen this firmware update from Toshiba?
[http://www.mytoshiba.com.au/support/items/faq/783](http://www.mytoshiba.com.au/support/items/faq/783)
It says it addresses issues with touchpad/keyboard  on the dock.

Best Regards

---

### Post by sbrookfield on 2014-03-11
I've tried the firmware at [http://www.mytoshiba.com.au/support/items/faq/783](http://www.mytoshiba.com.au/support/items/faq/783), does not change the issue. If you're interested about what works with me on ubuntu 13.10/14.04

Touchpad/trackpoint is detected, but does not work with Xorg
Touchscreen works out of the box but multitouch setup difficult
Keyboard works out of the box but not hotkeys
Display detected automatically but cannot change brightness easily
Graphics all work out of the box with 3d acceleration, haven't tried HDMI out
CPU/Ram/USB/Wireless all work out of the box, haven't tried SD card

---

### Post by caryb on 2014-03-24
Have installed Kubuntu & having same touchpad issues. Hopefully will have a answer soon. I have just updated to 14.04 beta to see if later kernel works but unfortunatly not.

---

### Post by caryb on 2014-03-24
BTW have dual boot with Android 4.4.2 the touchpad works ok in Android

---

### Post by caryb on 2014-03-24
existing bug report for the touchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1280839](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1280839)

---

### Post by rgbrown on 2014-06-02
I managed to get basic functionality by enabling the HID_MULTI_INPUT quirk for the device:

sudo rmmod usbhid && sudo modprobe -v usbhid quirks="0x0930:0x0807:0x0040"

If you do this the touchpad and trackpoint is just recognised as a basic mouse (but better than nothing!). The clickpad buttons don't work, but the trackpoint buttons do.

This device should be using the synaptics driver but I don't know how to do that

---

### Post by caryb on 2014-06-03
This works fine for me, does anyone know how to make this stick?

TIA Cary

---

### Post by rgbrown on 2014-06-09
Hi there

I've only been testing it from a live USB - I'm a little nervous about actually installing this, I've not installed Ubuntu on a Win8 / UEFI device before. Off-topic, but did you have any issues installing Ubuntu? Does it stop the recovery environment from working? 

I think you should be able to make it stick by adding the line usbhid.quirks=0x0930:0x0807:0x0040 to the line beginning with GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub (as per [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters))

---

### Post by josh62 on 2014-06-10
To get this sorted on my machine, I added the command without the "sudo" to /etc/rc.local

I now have a working trackpad :)

---

