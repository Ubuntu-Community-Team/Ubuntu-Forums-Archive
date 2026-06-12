---
title: "mousepad click not working on lenovo L450"
date: 2016-12-07
forum: Hardware
---

### Post by thomas-f0mkzpid on 2016-12-07
Suddenly I have lost tap-to-click functionality in my touchpad on my lenovo L450 laptop. And I can't seem to pinpoint where things went wrong.

I started out with a standard ubuntu 16.10 install, the other day, I wanted to have a peak at the gnome3 desktop, and installed ubuntu-gnome-desktop. After this was installed, I have been unable to use "tap-to-click". Everything else seems to work, even two finger scrolling in documents.

In system settings, I have enabled the "Tap to click" functionality for my mousepad, but it doesn't enable the tap-to-click..

Trying to run synclient gives me :
```

thomas at thomas-ThinkPad-L450 in ~ 
>synclient 
Couldn't find synaptics properties. No synaptics driver loaded?

```

Checking xorg logfiles, it seems that it does find synaptics hardware:

```

[    14.944] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event3 is a keyboard
[    14.944] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    14.944] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    14.944] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    14.944] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    14.944] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[    14.944] (II) Using input driver 'libinput' for 'SynPS/2 Synaptics TouchPad'
[    14.944] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.944] (**) Option "Device" "/dev/input/event5"
[    14.944] (**) Option "_source" "server/udev"
[    14.945] (II) input device 'SynPS/2 Synaptics TouchPad', /dev/input/event5 is tagged by udev as: Touchpad
[    14.945] (II) input device 'SynPS/2 Synaptics TouchPad', /dev/input/event5 is a touchpad
[    14.988] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    14.988] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    14.988] (**) Option "AccelerationScheme" "none"
[    14.988] (**) SynPS/2 Synaptics TouchPad: (accel) selected scheme none/0
[    14.988] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    14.988] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    14.988] (II) input device 'SynPS/2 Synaptics TouchPad', /dev/input/event5 is tagged by udev as: Touchpad
[    14.988] (II) input device 'SynPS/2 Synaptics TouchPad', /dev/input/event5 is a touchpad
[    14.988] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    14.988] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    14.989] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    14.989] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    14.989] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    14.989] (**) TPPS/2 IBM TrackPoint: Applying InputClass "libinput pointer catchall"
[    14.989] (II) Using input driver 'libinput' for 'TPPS/2 IBM TrackPoint'
[    14.989] (**) TPPS/2 IBM TrackPoint: always reports core events
[    14.989] (**) Option "Device" "/dev/input/event6"
[    14.989] (**) Option "_source" "server/udev"
[    14.989] (II) input device 'TPPS/2 IBM TrackPoint', /dev/input/event6 is tagged by udev as: Mouse Pointingstick
[    14.989] (II) input device 'TPPS/2 IBM TrackPoint', /dev/input/event6 is a pointer caps
[    15.028] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input7/event6"
[    15.028] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 12)
[    15.028] (**) Option "AccelerationScheme" "none"
[    15.028] (**) TPPS/2 IBM TrackPoint: (accel) selected scheme none/0
[    15.028] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    15.028] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    15.028] (II) input device 'TPPS/2 IBM TrackPoint', /dev/input/event6 is tagged by udev as: Mouse Pointingstick
[    15.028] (II) input device 'TPPS/2 IBM TrackPoint', /dev/input/event6 is a pointer caps
[    15.028] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    15.028] (II) No input driver specified, ignoring this device.

```

also dmesg indicates synaptics hardware :

```

thomas at thomas-ThinkPad-L450 in ~ 
>dmesg |grep -i synap
[    3.851393] psmouse serio1: synaptics: queried max coordinates: x [..5676], y [..4758]
[    3.892486] psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1096..]
[    3.967277] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xf003a3/0x943300/0x12e800/0x10000, board id: 3053, fw id: 2560
[    3.967284] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    4.015575] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[  742.655570] psmouse serio1: synaptics: queried max coordinates: x [..5676], y [..4758]
[  742.693732] psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1096..]
[ 5283.946143] psmouse serio1: synaptics: queried max coordinates: x [..5676], y [..4758]
[ 5283.984331] psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1096..]
[ 6054.907679] psmouse serio1: synaptics: queried max coordinates: x [..5676], y [..4758]
[ 6054.945746] psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1096..]
thomas at thomas-ThinkPad-L450 in ~ 

```


I have removed all packages that was installed with ubuntu-gnome-desktop from my system again, but the problem persists..

Where should I have a look, it's a bit frustrating that the system doesn't work.. I could take the windows route, and just re-install everything :) But I think it is just a configuration somewhere, that I have missed..

---

### Post by thomas-f0mkzpid on 2016-12-11
Found the problem, after some debugging, and trying to remove unneeded xserver packages.. The one that did the trick was xserver-xorg-input-libinput. After removing it's config file in /usr/share/x11/xorg.conf.d my tap-to-click returned.

So finally 

sudo apt purge xserver-xorg-input-libinput

did the trick

---

