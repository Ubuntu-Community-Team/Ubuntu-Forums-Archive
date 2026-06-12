---
title: "Two finger scrolling with Kubuntu Jaunty/KDE 4.3.1"
date: 2009-09-25
forum: Hardware
---

### Post by aurelieng on 2009-09-25
Dear all,

I have a Dell Precision M6400 with a synaptic touchpad, and I am trying to activate two finger scrolling, instead of the usual vertical scrolling zone.

I followed the following instructions, without success:
[http://ubuntuforums.org/showpost.php?p=7217419&postcount=4](http://ubuntuforums.org/showpost.php?p=7217419&postcount=4)
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[http://jann.is/daily/archives/823-Kubuntu-8.10-beta-KDE-4.1-synaptics-TouchPad-problem.html](http://jann.is/daily/archives/823-Kubuntu-8.10-beta-KDE-4.1-synaptics-TouchPad-problem.html)
[http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu](http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1055168](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1055168)

Here is my configuration:

* dmesg:
```

Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd44791/0xf0040d
serio: Synaptics pass-through port at isa0060/serio1/input0
input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

```

* cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

```

* xinput list-props 6:
```

Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (93):            1
        Synaptics Edges (238):          1632, 0, 5312, 0
        Synaptics Finger (239):         24, 0, 29
        Synaptics Tap Time (240):               180
        Synaptics Tap Move (241):               221
        Synaptics Tap Durations (242):          180, 0, 180
        Synaptics Tap FastTap (243):            0
        Synaptics Middle Button Timeout (244):          75
        Synaptics Two-Finger Pressure (245):            90
        Synaptics Scrolling Distance (246):             100, 0
        Synaptics Edge Scrolling (247):         1, 0, 0
        Synaptics Two-Finger Scrolling (248):           1, 1
        Synaptics Edge Motion Pressure (249):           29, 0
        Synaptics Edge Motion Speed (250):              1, 0
        Synaptics Edge Motion Always (251):             0
        Synaptics Button Scrolling (252):               1, 1
        Synaptics Button Scrolling Repeat (253):                1, 1
        Synaptics Button Scrolling Time (254):          100
        Synaptics Off (255):            0
        Synaptics Guestmouse Off (256):         0
        Synaptics Locked Drags (257):           0
        Synaptics Locked Drags Timeout (258):           5000
        Synaptics Tap Action (259):             2, 3, 0, 0, 1, 3, 2
        Synaptics Click Action (260):           1, 1, 1
        Synaptics Circular Scrolling (261):             0
        Synaptics Circular Scrolling Trigger (262):             0
        Synaptics Circular Pad (263):           0
        Synaptics Palm Detection (264):         0
        Synaptics Palm Dimensions (265):                10, 0
        Synaptics Pressure Motion (266):                29, 0
        Synaptics Grab Event Device (267):              1

```

* grep aptics /var/log/Xorg.0.log:
```

(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(**) Option "SHMConfig" "On"
(**) Option "EmulateTwoFingerMinZ" "90"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

```

Ideas anyone ?

Aurel.

---

### Post by Ayuthia on 2009-09-25
Have you tried:
```
synclient -m100
```
to see if it is seeing multiple fingers?  The number of fingers will be found under the f column.

---

### Post by aurelieng on 2009-09-25
> **Ayuthia said:**
> Have you tried:
```
synclient -m100
```
to see if it is seeing multiple fingers?  The number of fingers will be found under the f column.

Thanks for your fast reply :)

I just tried, and I see only 0 and 1 in the f column :( Does that mean that there is no hardware support for multiple fingers ?

---

### Post by Ayuthia on 2009-09-25
> **aurelieng said:**
> Thanks for your fast reply :)

I just tried, and I see only 0 and 1 in the f column :( Does that mean that there is no hardware support for multiple fingers ?

That is what I am thinking right now.  I have one laptop that only shows one finger my older laptop shows multiple.  I have not found any documentation that shows what hardware works and what doesn't.

---

### Post by aurelieng on 2009-09-26
Two interesting posts:

* [http://lists.freedesktop.org/archives/xorg/2009-February/043781.html](http://lists.freedesktop.org/archives/xorg/2009-February/043781.html) : points out a kernel bug (<2.6.29) allowing some devices to announce multi-finger capabilities (synclient -l |grep VertTwoFingerScroll) even if they don't actually do multi-finger

* [http://ubuntuforums.org/showthread.php?t=957691](http://ubuntuforums.org/showthread.php?t=957691) : a pressure-based workaround for two fingers, which is not working for me since the pressure measured in the z column of the synclient output does not unambiguously depends on the number of fingers on the touchpad. It might work for you ?

No solution, though. Any other idea ?

---

### Post by aurelieng on 2009-09-26
I found a (dirty) workaround: [http://ubuntuforums.org/showthread.php?p=8008900](http://ubuntuforums.org/showthread.php?p=8008900)

---

### Post by Ayuthia on 2009-09-26
I did a search for multi in this [document]("http://www.synaptics.com/decaf/utilities/ACF126.pdf") and I am assuming that mine most likely does not have multi-finger capabilities, but it has palm detection.  Apparently the W in synclient provides some information about what is on your touchpad.  If the values come in at 4-15, then it can detect a palm based on the value of W.  Mine shows those values.  If it shows 0 or 1 then it reports that there is more than one finger on the touchpad.  If it is 2, it detects a pen.

There is a bit that is set and the driver reads those bits and determines what your touchpad is able to do.

I am still somewhat surprised that HP would make a multi-touch touchscreen but only provide a single touch mouse touchpad for it.

---

### Post by Ayuthia on 2009-09-26
> **aurelieng said:**
> I found a (dirty) workaround: [http://ubuntuforums.org/showthread.php?p=8008900](http://ubuntuforums.org/showthread.php?p=8008900)

This one is interesting!  I might check this one out sometime.

---

### Post by aurelieng on 2009-10-31
It doesn't work anymore with Karmic, probably because it relies on DeviceKit instead of HAL. Any idea ?

---

### Post by Ayuthia on 2009-10-31
I have not checked it out yet.  I did notice that my xorg.conf has an entry for fglrx.  You might still be able to add the entry in your xorg.conf.

You might also check lshal to see if the configuration is there for your synaptics device.  If it is not, then something is most likely overwriting it.

---

