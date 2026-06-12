---
title: "touchpad as controller?"
date: 2009-09-28
forum: Hardware
---

### Post by kubriel on 2009-09-28
hello
im using ubuntu jaunty x64 on my asus f3tc laptop with synaptics touchpad.

i want to use touchpad for drive floats in pure data, not for cursor movement.
so now i need to read only touchpad data, not mouse
si i search through /dev/input
like cat /dev/input/event10
i tried all events, but only usb mouse was printing characters (i can read them in puredata with object linuxevent)
touchpad prints characters only in console (ctrl alt F2) on /dev/input/event10
or when i remove xserver-input-synaptics package - but then i cant turn touchpad off with synclient TouchpadOff=1

is it possible to manage this?

my xorg.0.log looks like this:
<code>
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "True"
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device Genius       Optical Mouse
(**) Genius       Optical Mouse: always reports core events
(**) Genius       Optical Mouse: Device: "/dev/input/event6"
(II) Genius       Optical Mouse: Found 3 mouse buttons
(II) Genius       Optical Mouse: Found x and y relative axes
(II) Genius       Optical Mouse: Configuring as mouse
(**) Genius       Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius       Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius       Optical Mouse" (type: MOUSE)
(**) Genius       Optical Mouse: (accel) keeping acceleration scheme 1
(**) Genius       Optical Mouse: (accel) filter chain progression: 2.00
(**) Genius       Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius       Optical Mouse: (accel) set acceleration profile 0
(II) Open ACPI successful (/var/run/acpid.socket)
</code>

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by Jamesss on 2010-06-20
I am also trying to achieve this with my touchpad on an Compaq NC6000 laptop. I can get the data in only if I remove xserver-xorg-input-synaptics. I've also tried to install the alps driver but I get the following error:

```
./configure: line 21842: syntax error near unexpected token `XINPUT,'
./configure: line 21842: `XORG_DRIVER_CHECK_EXT(XINPUT, inputproto)'

```

I would like to enable two-fingered scrolling and disable the touchpad tap like I had with the Synaptics driver, either with the Alps driver or another option?

any ideas?

thanks

James

---

