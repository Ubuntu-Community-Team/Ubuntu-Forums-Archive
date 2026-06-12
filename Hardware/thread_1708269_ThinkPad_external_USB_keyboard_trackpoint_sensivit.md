---
title: "ThinkPad external USB keyboard: trackpoint sensivity and sound control buttom config"
date: 2011-03-16
forum: Hardware
---

### Post by ibm86 on 2011-03-16
Hello all, and sorry for my English. 

How I can set up sensivity and speed for Trackpoint on my external keyboard. 

I try to see


```


evg@albereo:~$ xinput list 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint    id=11   [slave  pointer  (2)]
&#9116;   &#8627; MLK Defender 2.4GHz mouse                 id=12   [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                    id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; pac207                                    id=9    [slave  keyboard (3)]
    &#8627; Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint    id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                    id=14   [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                 id=16   [slave  keyboard (3)]

```


```


evg@albereo:~$ xinput list-props 11 
Device 'Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint':
        Device Enabled (140):   1
        Coordinate Transformation Matrix (142): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (268):     0
        Device Accel Constant Deceleration (269):       1.000000
        Device Accel Adaptive Deceleration (270):       1.000000
        Device Accel Velocity Scaling (271):    10.000000
        Evdev Reopen Attempts (261):    10
        Evdev Axis Inversion (272):     0, 0
        Evdev Axes Swap (274):  0
        Axis Labels (275):      "Rel X" (150), "Rel Y" (151)
        Button Labels (276):    "Button Left" (143), "Button Middle" (144), "Button Right" (145), "Button Wheel Up" (146), "Button Wheel Down" (147), "Button Horiz Wheel Left" (148), "Button Horiz Wheel Right" (149), "Button 3" (266), "Button 4" (267), "Button 2" (265), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262)
        Evdev Middle Button Emulation (277):    2
        Evdev Middle Button Timeout (278):      50
        Evdev Wheel Emulation (279):    0
        Evdev Wheel Emulation Axes (280):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (281):    10
        Evdev Wheel Emulation Timeout (282):    200
        Evdev Wheel Emulation Button (283):     4
        Evdev Drag Lock Buttons (284):  0
        Evdev Sensitivity (594):        1
        Evdev Speed (595):      1


```


And set-up 

```

 xinput set-int-prop 11 "Evdev Sensitivity" 8 127

```

But thete is no effect.

Also I try set 
```

    # echo -n 120 > /sys/devices/platform/i8042/serio1/serio2/speed 
    # echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
 
```

But only trackpoint on internal keyboard trackpoint settings changed, no in external. 

gpointing-device-settings can't change speed
configure-trackpoint can't see it. 
May be uou know how I can configure it another. 

Also how to configure sound control on this ketboard. 

ubuntu 10.10, last kernel.

---

### Post by ibm86 on 2011-03-18
sorry for up.

---

### Post by prokher on 2012-07-26
I am also interested. Having different sensitivity of trackpoint on embedded laptop's keyboard and external one is really annoying.

---

