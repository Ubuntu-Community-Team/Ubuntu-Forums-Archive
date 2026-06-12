---
title: "No mouse movement on UC-LOGIC TWHA60"
date: 2014-01-25
forum: Hardware
---

### Post by adamjacobs173 on 2014-01-25
Hi,

I've been trying to get my UC-LOGIC TWHA60 graphics tablet up and running and everything seems to work except the movement of the mouse. Pressing the pen down produces a click, most of the buttons work etc. I'm on the 3.8.0 kernel so as I understand it the drivers should be present. The output of xinput -list is

```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=15   [slave  pointer  (2)]
&#9116;   &#8627; MLK USB Multi-Smart Mouse                 id=10   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWHA60                           id=11   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWHA60                           id=12   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWHA60                           id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
```

It seems to come up as three devices; I have no idea if this is a problem or not :rolleyes: Any help would be greatly appreciated!

Here is the output of xinput on 11, 12 and 13:

```

UC-LOGIC TWHA60                                 id=11   [slave  pointer  (2)]
        Reporting 4 classes:
                Class originated from: 11. Type: XIButtonClass
                Buttons supported: 13
                Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
                Button state:
                Class originated from: 11. Type: XIValuatorClass
                Detail for Valuator 0:
                  Label: Abs X
                  Range: 0.000000 - 2048.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 640.000000
                Class originated from: 11. Type: XIValuatorClass
                Detail for Valuator 1:
                  Label: Abs Y
                  Range: 0.000000 - 2048.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 400.000000
                Class originated from: 11. Type: XIValuatorClass
                Detail for Valuator 2:
                  Label: Abs Pressure
                  Range: 0.000000 - 2047.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 0.000000

```
```

UC-LOGIC TWHA60                                 id=12   [slave  pointer  (2)]
        Reporting 6 classes:
                Class originated from: 12. Type: XIButtonClass
                Buttons supported: 7
                Button labels: "Button 0" "Button Unknown" "Button Unknown" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
                Button state:
                Class originated from: 12. Type: XIKeyClass
                Keycodes supported: 248
                Class originated from: 12. Type: XIValuatorClass
                Detail for Valuator 0:
                  Label: Rel X
                  Range: -1.000000 - -1.000000
                  Resolution: 1 units/m
                  Mode: relative
                Class originated from: 12. Type: XIValuatorClass
                Detail for Valuator 1:
                  Label: Rel Y
                  Range: -1.000000 - -1.000000
                  Resolution: 1 units/m
                  Mode: relative
                Class originated from: 12. Type: XIValuatorClass
                Detail for Valuator 2:
                  Label: Rel Horiz Wheel
                  Range: -1.000000 - -1.000000
                  Resolution: 1 units/m
                  Mode: relative
                Class originated from: 12. Type: XIScrollClass
                Scroll info for Valuator 2
                  type: 2 (horizontal)
                  increment: 1.000000
                  flags: 0x0

```
```

UC-LOGIC TWHA60                                 id=13   [slave  pointer  (2)]
        Reporting 6 classes:
                Class originated from: 13. Type: XIButtonClass
                Buttons supported: 5
                Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down"
                Button state:
                Class originated from: 13. Type: XIValuatorClass
                Detail for Valuator 0:
                  Label: Abs X
                  Range: 0.000000 - 40000.000000
                  Resolution: 157000 units/m
                  Mode: absolute
                  Current value: 640.000000
                Class originated from: 13. Type: XIValuatorClass
                Detail for Valuator 1:
                  Label: Abs Y
                  Range: 0.000000 - 25000.000000
                  Resolution: 157000 units/m
                  Mode: absolute
                  Current value: 400.000000
                Class originated from: 13. Type: XIValuatorClass
                Detail for Valuator 2:
                  Label: Abs Z
                  Range: 0.000000 - 2048.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 1545.000000
                Class originated from: 13. Type: XIValuatorClass
                Detail for Valuator 3:
                  Label: Abs Rotary X
                  Range: 0.000000 - 2048.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 64.000000
                Class originated from: 13. Type: XIValuatorClass
                Detail for Valuator 4:
                  Label: Abs Pressure
                  Range: 0.000000 - 2047.000000
                  Resolution: 0 units/m
                  Mode: absolute
                  Current value: 0.000000

```

---

### Post by adamjacobs173 on 2014-01-26
A workaround to this has been posted to the DIGImend mailing list; running

```

# modprobe -r usbhid
# modprobe usbhid "quirks=0x5543:0x0781:0x0040"

```

will cause the pen to work. I'm not sure if I should mark this as solved just yet as there may be a better solution.

---

### Post by adamjacobs173 on 2014-01-27
I should clarify that while this hack makes it work for a while, something (possibly applying over a certain threshold of pressure, not too sure) causes it to revert to not moving the mouse. There also seems to be no pressure response in any of the applications I've tried.

---

### Post by uudruid74 on 2014-07-02
I'm having the same trouble..

---

