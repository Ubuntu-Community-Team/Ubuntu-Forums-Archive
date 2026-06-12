---
title: "Microsoft Comfort Optical Mouse 3000 v1.0"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by Justin Trouble on 2007-05-31
I've been using my Microsoft Comfort Optical Mouse 3000 v1.0 (P/N: X802474 - 002 - [http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041) but a different colour) for six months without any wheel function! It's about time I configured it beyond a basic 2 button mouse function.

However I'm at the stage where bizarrely the wheel left and right works but the most importantly wheel scrolling up and down don't! :-(

After searching here and Google it seems I've had more success than most!

My first port of call was to check my mouse device:
```

# cat /proc/bus/input/devices
I: Bus=0003 Vendor=045e Product=00d1 Version=0111
N: Name="Microsoft Microsoft Optical Mouse with Tilt Wheel"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 ts1 event4
B: EV=7
B: KEY=170000 0 0 0 0 0 0 0 0
B: REL=143
```

I then edited the mouse section in /etc/X11/xorg.conf to use evdev with this mouse:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Protocol"              "auto"
        Option          "Name" "Microsoft Microsoft Optical Mouse with Tilt Wheel"
EndSection

```

After re-starting X I used the 'xev' program to check the button mapping.

The resulting button numbers are:
Left button: 1
Right button: 3
Wheel button: 2
Wheel left: 7
Wheel right: 6
Wheel scroll up: **No event detected!**
Wheel scroll down: **No event detected!**
Extra left button: 9

There's simply no event generated from scrolling the mouse wheel up and down. :-(

My next step was to check the Xorg log:
```

(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:1d.1-2/input0: Core Pointer
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: Found 4 relative axes.
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:1d.1-2/input0: HWHEELRelativeAxisButtons: 6 7.
(**) Configured Mouse-usb-0000:00:1d.1-2/input0: WHEELRelativeAxisButtons: 4 5.
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: Found 5 mouse buttons
(**) Configured Mouse-usb-0000:00:1d.1-2/input0: Configuring 4 relative axes.
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: Configured 9 mouse buttons
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse-usb-0000:00:1d.1-2/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Configured Mouse-usb-0000:00:1d.1-2/input0: 4 valuators.
(**) ../../src/evdev_btn.c (166): Registering 9 buttons.
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Configured Mouse-usb-0000:00:1d.1-2/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
```

evdev finds WHEELRelativeAxisButtons as 4 and 5 which sounds right to me looking at the results of 'xev'.

I hope my progress so far helps anyone with this mouse, but can anybody please help me complete this?

Many thanks.

---

### Post by defendguin on 2008-07-20
How did this go?  I'm still looking to get all my mouse buttons mapped properly.  The wheel worked out of the box but button 9 is the same as button 3 and i'd actually like to get it to be the same as button 2 the stupid mouse wheel click is a little heavy for my tastes.

---

