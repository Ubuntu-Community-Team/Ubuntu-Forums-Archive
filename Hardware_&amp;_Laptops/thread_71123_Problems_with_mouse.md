---
title: "Problems with mouse"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by eantoranz on 2005-10-02
I'm having mouse problems since I installed Kubuntu.

This is a dell inspiron 8100 with a Genius Netscroll mouse.

The mouse buttons normally don't react to clicks... but I have noticed that I can "click" by dragging a little, releasing and moving.... quite weird, right? Something that happens sometimes is that the pointer dissapears... but I can make it come back by moving with the touchpad (buttons fail there too. The same trick applies).

This is the dmess error:
```

psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.

```

This is my pointer section form xorg.conf:
```

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol"    "NetScrollPS/2"
#    Option "Device"      "/dev/mouse"
        Option "Device" "/dev/psaux"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"        "256"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"  "Xqueue"
        Option "Protocol" "PS2"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"  "9600"
#    Option "SampleRate"        "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection

```

I added the Protocol option to give it a try.... but it didn't work. I still have the same problem.

Any ideas? :confused:

---

### Post by XDevHald on 2005-10-02
**This needs to be moved to the Hoary KDE forum.**

---

