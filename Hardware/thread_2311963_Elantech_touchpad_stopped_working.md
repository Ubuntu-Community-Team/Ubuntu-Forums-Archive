---
title: "Elantech touchpad stopped working"
date: 2016-01-31
forum: Hardware
---

### Post by andybuckle on 2016-01-31
[COLOR=#000000][FONT=sans-serif]touchpad stopped working soon after install[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]kubuntu 15.10
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]```
[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][COLOR=#333333]> cat /proc/bus/input/devices[/COLOR]
...
I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event8  
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003
..
[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=sans-serif]

> xinput --list
...
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]                           
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]                           
&#9116;   &#8627; ETPS/2 Elantech Touchpad                  id=14   [slave  pointer  (2)] 
....
[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=sans-serif]
> cat /var/log/Xorg.0.log | grep -i elantech
[     9.801] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[     9.801] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     9.801] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     9.802] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[     9.802] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     9.802] (**) ETPS/2 Elantech Touchpad: always reports core events
[     9.824] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3276 (res 33)
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1872 (res 32)
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[     9.825] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     9.825] (**) ETPS/2 Elantech Touchpad: always reports core events
[     9.840] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[     9.840] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     9.840] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[     9.840] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.053
[     9.841] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     9.841] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     9.841] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     9.841] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     9.841] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     9.843] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[     9.843] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[/FONT][/COLOR]
```

It's a laptop. Not an Asus (like most of the elantech problems seem to be). Its a custom build from here
[https://www.pcspecialist.co.uk/notebooks/lafiteII/](https://www.pcspecialist.co.uk/notebooks/lafiteII/)

I have tried 
- re-starting psmouse module.
- [http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/) (did not install)
- ```
[COLOR=#000000]*echo 1 > /sys/devices/platform/i8042/serio4/reg_07*[/COLOR]
```[COLOR=#000000]* from here *[/COLOR]http://ubuntuforums.org/showthread.php?t=2271795 did not work. possiblly because the path on my system is a little different. mine should be serio1, but I am not sure what after that.

Nothing works.

---

### Post by andybuckle on 2016-01-31
I am an idiot

[fn]-F1 disables the touchpad. I must have hit that by accident.

---

