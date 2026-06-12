---
title: "Mouse buttons occupied by one application"
date: 2010-01-04
forum: Hardware
---

### Post by virx on 2010-01-04
Hello all

I am using Ubuntu 9.10 and have a problem with Logitech LX9 wireless mouse. After powering on computer in few minutes I am able to use mousebuttons on only one application (Firefox or Pidgin or Deluge, etc...). I can move cursor but buttons keep working only on last used application. For example I am able to click on pidgin tray icon. 

Some keyboards shortcuts (ALT+TAB, etc..) stop working also. So far only solution has been. Ctrl+Alt+F1 and after logging in
```
pkill -U *myusername*
```
Logging again through GDM everything keeps working.

It did not happen to last 3 years Ubuntu versions.

---

### Post by virx on 2010-01-05
Could it be something related to evdev module unloading?

Here is ending of Xorg.log while everything is OK
```
(II) config/hal: Adding input device Logitech USB RECEIVER
(**) Logitech USB RECEIVER: always reports core events
(**) Logitech USB RECEIVER: Device: "/dev/input/event4"
(II) Logitech USB RECEIVER: Found 20 mouse buttons
(II) Logitech USB RECEIVER: Found x and y relative axes
(II) Logitech USB RECEIVER: Found scroll wheel(s)
(II) Logitech USB RECEIVER: Configuring as mouse
(**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
(**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
(**) Logitech USB RECEIVER: (accel) keeping acceleration scheme 1
(**) Logitech USB RECEIVER: (accel) filter chain progression: 2.00
(**) Logitech USB RECEIVER: (accel) filter stage 0: 20.00 ms
(**) Logitech USB RECEIVER: (accel) set acceleration profile 0
(II) Logitech USB RECEIVER: initialized for relative axes.

```

And here is Xorg.log.old from the problem:
```
(II) config/hal: Adding input device Logitech USB RECEIVER
(**) Logitech USB RECEIVER: always reports core events
(**) Logitech USB RECEIVER: Device: "/dev/input/event4"
(II) Logitech USB RECEIVER: Found 20 mouse buttons
(II) Logitech USB RECEIVER: Found x and y relative axes
(II) Logitech USB RECEIVER: Found scroll wheel(s)
(II) Logitech USB RECEIVER: Configuring as mouse
(**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
(**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
(**) Logitech USB RECEIVER: (accel) keeping acceleration scheme 1
(**) Logitech USB RECEIVER: (accel) filter chain progression: 2.00
(**) Logitech USB RECEIVER: (accel) filter stage 0: 20.00 ms
(**) Logitech USB RECEIVER: (accel) set acceleration profile 0
(II) Logitech USB RECEIVER: initialized for relative axes.
(II) Logitech USB RECEIVER: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) saa7134 IR (ASUSTeK P7131 Hybri: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

