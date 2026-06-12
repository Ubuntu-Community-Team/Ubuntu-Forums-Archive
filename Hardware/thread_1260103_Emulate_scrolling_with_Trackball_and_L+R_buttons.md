---
title: "Emulate scrolling with Trackball and L+R buttons"
date: 2009-09-07
forum: Hardware
---

### Post by map84 on 2009-09-07
Hi,

i'm using a Dell Latitude D420 and it has a Trackpoint witch has not the possibility to click. Is it possible to use the left and right mousebuttons down below to emulate a middle-click to use the Trackpoint as a scrolling-wheel and how do i have to tell this either HAL or Xorg?

Thanks in advance for your answers!

---

### Post by map84 on 2009-09-09
I created a file called mouse-wheel.fdi in

 ```
/etc/hal/fdi/policy/
```

with following content:
```

<match key="info.product" string="PS/2 Mouse">
<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
<merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
<merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
<merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
<merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

```
nevertheless it didn't enable scrolling with the Trackpoint.

I think the standard-function "paste" witch comes with the emulated middle-mouse-button blocks the scrolling.

---

### Post by map84 on 2009-09-10
Here is the related Xorg.conf output.

```
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) Option "Emulate3Buttons" "true"
(II) PS/2 Mouse: Forcing middle mouse button emulation on.
(**) Option "EmulateWheel" "true"
(**) Option "EmulateWheelButton" "2"
(**) Option "EmulateWheelTimeout" "200"
(**) Option "YAxisMapping" "4 5"
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Option "XAxisMapping" "6 7"
(**) PS/2 Mouse: XAxisMapping: buttons 6 and 7
(**) PS/2 Mouse: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
```

Anybody could help a bit, please?

---

### Post by map84 on 2009-09-15
It seems that it's not possible to enable scrolling with emulated middle-mouse-button without having physically a middle-mouse-button.

---

### Post by utnubuuser on 2009-09-18
Scroll using the middle button and trackpoint on thinkpad x31 works -- 8.04

Also middle button click for new tab/window.> Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"
EndSection

Not sure how to translate that for 9.04 configurations though.

---

