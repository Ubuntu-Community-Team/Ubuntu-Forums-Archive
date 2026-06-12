---
title: "Touchpad not working at all (Acer Laptop), unlikely hardware or driver problem"
date: 2011-01-06
forum: Hardware
---

### Post by quanben on 2011-01-06
This is a problem I have with ubuntu 10.10 on my acer aspire 4741g. 
The synapitcs touchpad doesn't work anymore. I couldn't figure out when it started to happen. 
I searched online for solutions, and have tried most of them, including:

1. detecting the device, which seems to be fine:
$ cat /proc/bus/input/devices

output relevant to the touchpad:
...
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=420 30000 0 0 0 0
B: ABS=11000003
...


2. enable in gconftool
sudo gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true

3. configuring in xorg.conf doesn't help

4. check up the log by:

$ cat /var/log/Xorg.0.log | grep -i synaptics
[    26.853] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    26.853] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.853] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.853] (**) SynPS/2 Synaptics TouchPad: Device: "/dev/input/event7"
[    26.892] (II) SynPS/2 Synaptics TouchPad: Found 3 mouse buttons
[    26.892] (II) SynPS/2 Synaptics TouchPad: Found absolute axes
[    26.892] (II) SynPS/2 Synaptics TouchPad: Found x and y absolute axes
[    26.892] (II) SynPS/2 Synaptics TouchPad: Found absolute touchpad.
[    26.892] (II) SynPS/2 Synaptics TouchPad: Configuring as touchpad
[    26.892] (**) SynPS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    26.892] (**) SynPS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.892] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    26.892] (II) SynPS/2 Synaptics TouchPad: initialized for absolute axes.
[    26.893] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    88.252] (II) SynPS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[   147.481] (II) SynPS/2 Synaptics TouchPad: Device reopened after 1 attempts.
...

no apparent problem found

5. when i turned to evtest, something weird happened. I was tracking event7 which is designated to the touchpad:

$ sudo evtest /dev/input/event7
Input driver version is 1.0.1
Input device ID: bus 0x11 vendor 0x2 product 0x7 version 0x1b1
Input device name: "SynPS/2 Synaptics TouchPad"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 325 (ToolFinger)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   3090
      Min     1472
      Max     5576
    Event code 1 (Y)
      Value   3754
      Min     1408
      Max     4880
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max      255
    Event code 28 (Tool Width)
      Value      0
      Min        0
      Max        0
Testing ... (interrupt to exit)

<<< the test program waits here for incoming event from touchpad, and as I swiped my finger on the pad (which is claimed to be enabled), nothing happened as I expected; but when I disable the touchpad by pressing Fn+F7 (combination key defined on acer laptop to switch on/off touchpad), and on the screen a picture did show up of a touchpad with a red cross indicating the disable operation, surprisingly, the event test program started to display a series of events which look corresponding to what I had done with the touchpad, as follows:

Event: time 1294311437.197744, type 1 (Key), code 330 (Touch), value 1
Event: time 1294311437.197751, type 3 (Absolute), code 0 (X), value 3198
Event: time 1294311437.197752, type 3 (Absolute), code 1 (Y), value 2350
Event: time 1294311437.197754, type 3 (Absolute), code 24 (Pressure), value 75
Event: time 1294311437.197755, type 3 (Absolute), code 28 (Tool Width), value 4
Event: time 1294311437.197756, type 1 (Key), code 325 (ToolFinger), value 1
Event: time 1294311437.197758, -------------- Report Sync ------------
Event: time 1294311437.210453, type 3 (Absolute), code 0 (X), value 3031
Event: time 1294311437.210458, type 3 (Absolute), code 1 (Y), value 2404
Event: time 1294311437.210460, type 3 (Absolute), code 24 (Pressure), value 81
Event: time 1294311437.210463, -------------- Report Sync ------------
Event: time 1294311437.223076, type 3 (Absolute), code 0 (X), value 2909
Event: time 1294311437.223082, type 3 (Absolute), code 1 (Y), value 2435
...

However, unfortunately, even in this touchpad disabled mode, in which the event test shows there are touchpad events captured, the touchpad doesn't have any real effect on the mouse cursor.

So from the appearance, I guess there might be something wrong with the touchpad switch or control program, whose internal on/off state might be opposite to the actual state, and prevent the touchpad from functioning. So in the first place, I would very like to know how to reset this switch program which I so far hasn't figured out.

Or is there any one can help or point out what is wrong with the approaches above?

Though as a programmer with certain experience on linux, I think I can understand most of technical terms, I'm still sort of a newbie to linux, I just wish to be given hints and details on issues unfamiliar when talking about the solution.

Thanks a lot!

---

### Post by funicorn on 2011-04-16
I have the same laptop of Acer 4741G. The touchpad is recognized as a wheel mouse. The scrolling bar does not work, and nothing happens if I disable the touchpad from  mouse configuration GUI. Touchpad stills works like a two-button mouse.

---

### Post by white.noise on 2011-06-11
See the link below, worked for me. Touch pad did not work at all and fn key showed it turning on and off. Other usb mice would work fine.

[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Troubleshooting](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Troubleshooting)

Good luck ;)

---

### Post by white.noise on 2011-06-12
Sorry I forgot to mention that I did not follow the instructions completely.

Instead of modifying: /etc/X11/xorg.conf.d/10-synaptics.conf

I modified: /etc/X11/xorg.conf.failsafe

The reason for this was that the folder specified did not exist and the one modified had other similar bits of code in it.

---

