---
title: "Keyboard doesn't work in Ubuntu Feisty"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Nimra on 2007-06-19
Hello,

I can't log in my Ubuntu 7.04!

When I want to log in with my username, nothing happens.

The login-screen appears, I can't type anything.

But the connector is connected.

I use an pc105-keyboard with an PS/2-connector

Thanks

---

### Post by vexorian on 2007-06-19
> **Nimra said:**
> Hello,

I can't log in my Ubuntu 7.04!

When I want to log in with my username, nothing happens.

The login-screen appears, I can't type anything.

But the connector is connected.

I use an pc105-keyboard with an PS/2-connector

Thanks
I am guessing grub does appear and you use the keyboard to choose ?

Did the keyboard work on live-cd? If you enter in ubuntu recovery mode can you use the keyboard?

Just saying that it is very odd that it would happen, it could instead be something about the screen freezing.

---

### Post by Nimra on 2007-06-21
Thanks

here are the answers:

I am guessing grub does appear and you use the keyboard to choose ?

yes


Did the keyboard work on live-cd?

6.10 Yes   7.04 sometimes

If you enter in ubuntu recovery mode can you use the keyboard?

No


Maybe someone could tell me how to include the keyboard of edgy in feisty

---

### Post by Nimra on 2007-06-23
Here is an extract from my /var/log/xorg.0.log

Maybe that can help somebody to solve my problem

Thanks



(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

### Post by Nimra on 2007-06-23
Well, I have to correct the answer from before...

Sometimes the keyboard works in recovery mode, sometimes not.

Sorry

---

### Post by pickarooney on 2007-06-23
Is it a wireless keyboard? PS/2? USB?

---

### Post by Nimra on 2007-06-24
Hi,

It's an PS/2-Keyboard, and it's an not-wireless keyboard....

---

### Post by Nimra on 2007-06-25
Hello,

I've looked again at my Xorg.0.log after a crash.

Then I've seen these two lines at the end


P.S.  The 2 lines are in the atatchment, because I didn't know, how to use nano.


Nimra



AUDIT: Sun Jun 24 18:02:00 2007: 7188 X: client 2 rejected from local host (uid 1000)
AUDIT: Sun Jun 24 18:02:00 2007: 7188 X: client 2 rejected from local host (uid 1000)

---

### Post by Nimra on 2007-09-06
Hi,

Now I'm using Gutsy Gibbon Alpha Tribe 5, here it works:lolflag::)

But Gutsy still has some bugs:( so I'll be happy, when the final realease will appear

Thanks for your help!

---

### Post by Nimra on 2008-04-29
It was my doubt. My DIN -> PS/2-Adaptor was defect](*,)	](*,)	](*,)

---

