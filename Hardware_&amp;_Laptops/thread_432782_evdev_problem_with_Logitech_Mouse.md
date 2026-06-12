---
title: "evdev problem with Logitech Mouse"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by Paradoxdruid on 2007-05-04
After the upgrade to Kubuntu Feisty, my Logitech mouse has been behaving strangely--  sometimes the additional mouse buttons work, sometimes they don't.  Lately, they don't at all--  though normal mouse function worked fine.  I use the evdev driver, and can see in the logs what's going wrong--  it's not seeing it as a mouse (or seeing it as a mouse "in time"), and configuring a default pointer instead.

The two relevant portions of my /var/log/Xorg.0.log are right at the beginning
```
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Radius-73"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Logitech MediaPlay Mouse"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
```
which is odd because the Logitech MediaPlay Mouse is specificed in xorg.conf as CorePointer.  then, near the bottom:
```
(**) Option "CorePointer"
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Core Pointer
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Found 3 relative axes.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configuring as pointer.
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Found 5 mouse buttons
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configuring 3 relative axes.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configured 7 mouse buttons
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
```

So evdev is finding my mouse, and says it is configuring it as Core Pointer, but then it says that no device is specified.

Any idea what's going wrong?  I'd appreciate any help or pointers to what to change.

The relevant bits of my xorg.conf are below:
```
Section "InputDevice"
    Identifier     "Logitech MediaPlay Mouse"
    Driver         "evdev"
#    Driver	   "mouse"
    Option         "Device" "/dev/input/event2"
    Option	   "Dev Name" "Logitech USB Receiver"
    Option	   "Device Phys" "usb-0000:00:1d.1-1/input0"
    Option         "CorePointer"
    Option         "Name" "Logitech USB Receiver"
#    Option         "HWHEELRelativeAxisButtons" "7 6"
    Option 	   "ZAxisMapping" "4 5"
    Option	   "Resolution" "800"
    Option	   "Buttons" "17"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MediaPlay Mouse" "CorePointer"
EndSection
```

---

### Post by Paradoxdruid on 2007-05-04
One bump before I let it vanish.  No one has any ideas?

I'm not very experienced with evdev.  Are there any particularly good resources where I could read up for myself?

Thanks for any help!

---

### Post by merlinus on 2007-05-04
I am interested in learning where I can find the evdev driver.  I have a LT MX1000.

Many thanks!

-merlin

---

### Post by Paradoxdruid on 2007-05-05
> **merlinus said:**
> I am interested in learning where I can find the evdev driver.  I have a LT MX1000.

Here ya go:
```
sudo aptitude install xserver-xorg-input-evdev
```

There's a specific guide on the forums here for setting up the MX1000 with evdev, try searching for it.  Good luck!

---

### Post by Paradoxdruid on 2007-05-16
My mouse had started working fine, then after boot up today was not being recognized anymore...

A relevant portion of the X.log: ```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Core Pointer
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Found 3 relative axes.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configuring as pointer.
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Found 5 mouse buttons
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configuring 3 relative axes.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Configured 7 mouse buttons
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
(II) XINPUT: Adding extended input device "Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: 3 valuators.
(**) ../../src/evdev_btn.c (166): Registering 7 buttons.
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MediaPlay Mouse-usb-0000:00:1d.1-1/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
```

So evdev is recognizing it as a CorePointer and configuring it, but XINPUT is calling it a keyboard, and the default pointer is being loaded...  What's going on?

Here's the relevant xorg.conf: ```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MediaPlay Mouse" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Logitech MediaPlay Mouse"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
    Option         "HWHEELRelativeAxisButtons" "7 6"
    Option         "Resolution" "800"
    Option         "CorePointer"
EndSection

```

---

