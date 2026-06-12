---
title: "Absolutely terribly touchpad"
date: 2009-07-11
forum: Hardware
---

### Post by The Tronyx on 2009-07-11
Hello everyone.  I recently purchased an Acer Timeline AS4810TZ-4696 and have it booted into the 2.6.30 kernel as suspend is not supported in the standard Jaunty kernel.  Long story short, the mouse is amazingly erratic.

Without provocation or touching, the mouse will jump all over the screen and even then, almost resist when you try and move it where you want it to go.  Then there are also times that it doesn't to it at all.  For example, my mouse hasn't acted up in the last 10 or 15 minutes but when I booted up my laptop, as soon as I had logged into Gnome, the entire thing went nuts.

There doesn't look to be anything in the Xorg log about it other than very standard stuff - at least I don't see any problems.

```

tronyx@wrekx:/var/log$ grep -i mouse Xorg.0.log
(==) intel(0): Silken mouse enabled
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
```

```

tronyx@wrekx:~$ xinput list > list.txt
**SNIP**
"Macintosh mouse button emulation"      id=4    [XExtensionPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
        Num_buttons is 12
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 1472
                Max_value is 5472
                Resolution is 1
        Axis 1 :
                Min_value is 1408
                Max_value is 4448
                Resolution is 1

```

Any thoughts?

---

### Post by miegiel on 2009-07-22
> **The Tronyx said:**
> Any thoughts?

[LIST=1]
[*]Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=1165087")
[*]With this new hardware you should try the newest release (or even an alpha/beta of the next release)
[/LIST]

---

