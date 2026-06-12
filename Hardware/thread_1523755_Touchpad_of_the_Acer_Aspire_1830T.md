---
title: "Touchpad of the Acer Aspire 1830T"
date: 2010-07-04
forum: Hardware
---

### Post by Darkas on 2010-07-04
Hi!

I'm having problems with my touchpad on the Acer Aspire 1830T (ubuntu 10.4): any configuration I'm doing isn't applied. So the changes are done in the menus and are actually saved, but I can configure what I want without any effect. This includes that I can't use any real touchpad feature (scrolling, etc.). The relevant part of my Xorg.0.log is: 
> (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.2.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)
(II) intel(0): EDID vendor "AUO", prod id 8284
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   65.50  1366 1390 1406 1406  768 770 774 776 -hsync -vsync (46.6 kHz)

I think the problem is > (II) No input driver/identifier specified (ignoring)

Additionally, there's also another problem with different kernels: On the 2.6.32-23 Kernel, the touchpad isn't even detected as one, but as a Generic PS/2 Mouse, so I'm using 2.6.32-21 right now, where the touchpad is detected as one.

Is there anyone who could help me with that please?

---

### Post by hounddog32 on 2010-08-26
I have the same problem with the 1830T with Maverick.

---

### Post by tpdi on 2010-08-31
I have an Acer 1830T (-3721), with the ALPS :( Touchpad.

Installing the psmouse.ko in message #152 here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/152](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/152)

enables one-finger vertical scrolling in the touchpad right-edge "vertical scroll area"; it does not enable GUI touchpad settings or two-finger anything (though some settings can be set from teh command line using xinput).

Off-Topic: I also had to install a restricted driver from the Broadcomn wireless card, and compile and install a driver for the Atheros ethernet card.

If anyone can help me with thermal control/fan settings, or powersaving under Ubuntu for the 1830T, I'd appreciate it.

---

### Post by Saorex on 2010-09-28
I installed Maverick (Netbook Edition) yesterday. Atheros ethernet card worked out of the box. I then installed the restricted driver for the Broadcom wireless card and it's working perfectly.

Ubuntu then asked me to do a partial upgrade. It solved manu ui-related bugs. I still haven't tried anything for the ALPS mouse pad though. I read a lot about it and there doesn't seem to be an easy solution. Any help would be appreciated.

---

### Post by scarleo on 2010-10-09
@tpdi: Hi, would you mind telling me how you did that? I've tried to follow the instructions there but I'm not able to do ' sudo insmod psmouse.ko', it just fails with an error message. I'd appreciate very much if you would like to give me some details. I do have the Acer Aspire 1830TZ with ALPS touchpad.

EDIT: Which kernel are you using?

---

