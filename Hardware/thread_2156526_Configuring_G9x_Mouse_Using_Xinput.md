---
title: "Configuring G9x Mouse Using Xinput"
date: 2013-06-22
forum: Hardware
---

### Post by Hypna on 2013-06-22
Hi, I'm very new to linux and ubuntu and I'm settling in to the new environment; trying to make myself at home. One of the quirks I'm trying to iron out is my mouse sensitivity, but I'm having a hard time finding documentation defining exactly what these device properties do. Xinput is also saying something I find strange. 

> 
hypna@Hypnix:~$ xinput --list[INDENT]Virtual core pointer                        id=2    [master pointer  (3)][/INDENT]
[INDENT=2]&#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
[/INDENT]
[INDENT=2]&#8627; Logitech G9x Laser Mouse                    id=8    [slave  pointer  (2)]
[/INDENT]
[INDENT=2]&#8627; Logitech G9x Laser Mouse                    id=9    [slave  pointer  (2)]
[/INDENT]
[INDENT=2]&#8627; Creative Technology Ltd. SB Tactic(3D) Wrath Wireless    id=11    [slave  pointer  (2)]
[/INDENT]
[INDENT]Virtual core keyboard                       id=3    [master keyboard (2)][/INDENT]
[INDENT=2]&#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
      &#8627; Power Button                                id=6    [slave  keyboard (3)]
      &#8627; Power Button                                id=7    [slave  keyboard (3)]
      &#8627; Silitek Standard USB Keyboard               id=10    [slave  keyboard (3)][/INDENT]


Why does xinput list my G9x mouse twice? How should I know which device's properties to alter? The following are the options relevant to the second part of my confusion.

> 
hypna@Hypnix:~$ xinput list-props 8[INDENT]Device 'Logitech G9x Laser Mouse':[/INDENT]
[INDENT=2]Device Enabled (139):    1
Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
Device Accel Profile (266):    0
Device Accel Constant Deceleration (267):    1.000000
Device Accel Adaptive Deceleration (268):    1.000000
Device Accel Velocity Scaling (269):    10.000000
Device Product ID (255):    1133, 49254
Device Node (256):    "/dev/input/event2"
Evdev Axis Inversion (270):    0, 0
Evdev Axes Swap (272):    0
Axis Labels (273):    "Rel X" (149), "Rel Y" (150), "Rel Horiz Wheel" (264), "Rel Vert Wheel" (265)
Button Labels (274):    "Button Left" (142), "Button Middle" (143), "Button Right" (144), "Button Wheel Up" (145), "Button Wheel Down" (146), "Button Horiz Wheel Left" (147), "Button Horiz Wheel Right" (148), "Button Side" (259), "Button Extra" (260), "Button Forward" (261), "Button Back" (262), "Button Task" (263), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258), "Button Unknown" (258)
Evdev Middle Button Emulation (275):    0
Evdev Middle Button Timeout (276):    50
Evdev Third Button Emulation (277):    0
Evdev Third Button Emulation Timeout (278):    1000
Evdev Third Button Emulation Button (279):    3
Evdev Third Button Emulation Threshold (280):    20
Evdev Wheel Emulation (281):    0
Evdev Wheel Emulation Axes (282):    0, 0, 4, 5
Evdev Wheel Emulation Inertia (283):    10
Evdev Wheel Emulation Timeout (284):    200
Evdev Wheel Emulation Button (285):    4
Evdev Drag Lock Buttons (286):    0
[/INDENT]


Which one of these properties will most prudently deactivate acceleration? Do I change the "Accel Profile", set the "Velocity Scaling" to 0, or something else? Any help or information is appreciated.

P.S. I'm aware that changing these properties does not produce a permanent settings change. I'll worry about putting together and executing a batch file after I sort this out.

UPDATE:

I finally found the [documentation]("http://xorg.freedesktop.org/wiki/Development/Documentation/PointerAcceleration") I needed for part two. It appears that the best way to turn off all acceleration is to set Device Accel Profile = -1. Changing this setting on the first entry for my mouse has been effective, but I'm still curious as to why there are two entries. [URL="http://xorg.freedesktop.org/wiki/Development/Documentation/PointerAcceleration"]
[/URL]

---

