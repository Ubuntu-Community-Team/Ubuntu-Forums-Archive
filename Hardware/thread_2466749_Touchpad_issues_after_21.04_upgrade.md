---
title: "Touchpad issues after 21.04 upgrade"
date: 2021-09-04
forum: Hardware
---

### Post by dividedrelic on 2021-09-04
Hi all,

This is my first post here. I am having troubles with my touchpad on my Lenovo Yoga 9i after updating to the 21.04 release.

The main point is that the Yoga 9i has a haptic touchpad, which means that it is pressure-based. After updating Ubuntu, I am facing an issue where the libinput driver only detects touches with a certain pressure, which means that I have to slightly press the touchpad to be able to use it (instead of simply touching it).

Before, I used X11 configs together with the synaptic drivers which worked just fine.

```

Section "InputClass" 
        Identifier "libinput touchpad catchall" 
        MatchIsTouchpad "on" 
        MatchDevicePath "/dev/input/event*" 
        Option "Tapping" "on" 
        Option "FingerLow" "0" 
        Option "FingerHigh" "0" 
        Option "HorizScrollDelta" "-76" 
        Option "TapButton1" "1" 
        Option "RightButtonAreaLeft" "0" 
        Option "RightButtonAreaTop" "0" 
        Driver "synaptics" 
EndSection

```

 However, these are not working anymore after the update. As far as I can see, libinput is used for input devices.

I managed to slightly mitigate this problem by creating the below libinput quirk to lower the touch pressure.

```

[Touchpad pressure override] 
MatchUdevType=touchpad 
AttrPressureRange=1:0 
AttrPalmPressureThreshold=255

```

However, this still does not detect light touches (i.e. when my finger  is merely touching the pad with only low pressure). I tried using the debugging  tool as in
[https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html#list-of-supported-device-quirks](https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html#list-of-supported-device-quirks).
From the output below, I think the main problem is that when I touch the pad without  applying any real pressure, libinput does not detect it as a touch because it wasn't able to record any pressure. Ideally, I'd want this event to be detected as a touch, because by design of a touchpad one should not need to apply a specific pressure to move the cursor.

```

+-------------------------------------------------------------------------------+ 
| Thresh |   0    |  0   |  255   |  255   |                                    | 
+-------------------------------------------------------------------------------+ 
| Touch  |  down  |  up  |  palm  | thumb  | min  | max  | p  | avg  |  median  | 
+-------------------------------------------------------------------------------+ 
|  608   |        |      |        |        | No pressure values recorded |      | 
|  609   |        |      |        |        | No pressure values recorded |      | 
|  610   |   x    |  x   |        |        |  0   |  67  | 0  |  49  |    56    | 
+-------------------------------------------------------------------------------+ 

```

I'd greatly appreciate any help to solve this issue. Also, could you please explain why the X11 configs are not working anymore?

---

