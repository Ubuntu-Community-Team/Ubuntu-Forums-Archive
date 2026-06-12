---
title: "Apple Magic Mouse A1296 not generating Scroll event's (16.04)"
date: 2018-04-27
forum: Hardware
---

### Post by mircsicz on 2018-04-27
I just got myself a Tuxedo Infinitybook Pro 13. It's running a Tuxedo compiled Kernel (4.13.0-38) and so far I'm really happy with the rig...

But I can't get my first generation Apple Magic Mouse to scroll. I've spent three nights with research and trial and lot's of error's so I came here to ask for help. Besides that I've posted to the german forum too but I guess non of those has a magic mouse...

Here's what I learned so far:

```
mircsicz@TUXEDO ~ $  sudo lsmod |grep hid
hid_magicmouse         16384  0
hid_generic            16384  0
usbhid                 49152  0
uhid                   20480  1
hid                   118784  4 hid_generic,usbhid,hid_magicmouse,uhid
intel_hid              16384  0
mac_hid                16384  0
sparse_keymap          16384  1 intel_hid
```

So the mouse is connected and the required kernel module get's loaded
```

mircsicz@TUXEDO ~ $  sudo lsinput
/dev/input/event15
   bustype : BUS_BLUETOOTH
   vendor  : 0x5ac
   product : 0x30d
   version : 774
   name    : "Mircsiczs Maus"
   phys    : "18:4F:32:F3:EC:AA"
   uniq    : "B8:17:C2:A8:2D:C5"
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC
```

According to [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) I've checked xinput too

```
mircsicz@TUXEDO ~ $  sudo xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Mircsiczs Maus                     	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; SuYin USB2.0 RGBIR Camera: SuYi         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

```
mircsicz@TUXEDO ~ $  sudo xinput list-props 13
Device 'Mircsiczs Maus':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (262):	0
	Device Accel Constant Deceleration (263):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Device Product ID (256):	1452, 781
	Device Node (257):	"/dev/input/event15"
	Evdev Axis Inversion (617):	0, 0
	Evdev Axes Swap (619):	0
	Axis Labels (620):	"Rel X" (145), "Rel Y" (146), "Rel Horiz Wheel" (512), "Rel Vert Wheel" (513)
	Button Labels (621):	"Button Left" (138), "Button Middle" (139), "Button Right" (140), "Button Wheel Up" (141), "Button Wheel Down" (142), "Button Horiz Wheel Left" (143), "Button Horiz Wheel Right" (144)
	Evdev Scrolling Distance (622):	1, 1, 1
	Evdev Middle Button Emulation (623):	0
	Evdev Middle Button Timeout (624):	50
	Evdev Third Button Emulation (625):	0
	Evdev Third Button Emulation Timeout (626):	1000
	Evdev Third Button Emulation Button (627):	3
	Evdev Third Button Emulation Threshold (628):	20
	Evdev Wheel Emulation (629):	0
	Evdev Wheel Emulation Axes (630):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (631):	10
	Evdev Wheel Emulation Timeout (632):	200
	Evdev Wheel Emulation Button (633):	4
	Evdev Drag Lock Buttons (634):	0

```

```
mircsicz@TUXEDO ~ $  sudo xinput query-state 13
2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=2522
	valuator[1]=1491
	valuator[2]=0
	valuator[3]=0
```

```
mircsicz@TUXEDO ~ $  sudo xinput get-button-map 13
1 2 3 5 4 6 7
```

As you can see my setting of reverse scrolling the GUI has been successful...

But evtest only show's the left and the right button, button scrolling is being ignored:

```
mircsicz@TUXEDO ~ $  sudo evtest /dev/input/event15
Input driver version is 1.0.1
Input device ID: bus 0x5 vendor 0x5ac product 0x30d version 0x306
Input device name: "Mircsiczs Maus"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 272 (BTN_LEFT)
    Event code 273 (BTN_RIGHT)
    Event code 274 (BTN_MIDDLE)
  Event type 2 (EV_REL)
    Event code 0 (REL_X)
    Event code 1 (REL_Y)
    Event code 6 (REL_HWHEEL)
    Event code 8 (REL_WHEEL)
  Event type 3 (EV_ABS)
    Event code 47 (ABS_MT_SLOT)
      Value      0
      Min        0
      Max       15
    Event code 48 (ABS_MT_TOUCH_MAJOR)
      Value      0
      Min        0
      Max     1020
      Fuzz       4
    Event code 49 (ABS_MT_TOUCH_MINOR)
      Value      0
      Min        0
      Max     1020
      Fuzz       4
    Event code 52 (ABS_MT_ORIENTATION)
      Value      0
      Min      -31
      Max       32
      Fuzz       1
    Event code 53 (ABS_MT_POSITION_X)
      Value      0
      Min    -1100
      Max     1258
      Fuzz       4
      Resolution      26
    Event code 54 (ABS_MT_POSITION_Y)
      Value      0
      Min    -1589
      Max     2047
      Fuzz       4
      Resolution      70
    Event code 57 (ABS_MT_TRACKING_ID)
      Value      0
      Min        0
      Max    65535
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Properties:
Testing ... (interrupt to exit)
Event: time 1524816296.374223, type 2 (EV_REL), code 0 (REL_X), value 1
Event: time 1524816296.374223, -------------- SYN_REPORT ------------
Event: time 1524816296.374277, type 2 (EV_REL), code 0 (REL_X), value 2
Event: time 1524816296.374277, -------------- SYN_REPORT ------------
Event: time 1524816296.374580, type 2 (EV_REL), code 0 (REL_X), value 1
Event: time 1524816296.374580, -------------- SYN_REPORT ------------
Event: time 1524816296.374803, type 2 (EV_REL), code 0 (REL_X), value 1
Event: time 1524816296.374803, -------------- SYN_REPORT ------------
Event: time 1524816296.384909, type 2 (EV_REL), code 0 (REL_X), value 1
Event: time 1524816296.384909, -------------- SYN_REPORT ------------
Event: time 1524816296.386116, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
Event: time 1524816296.386116, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1
Event: time 1524816296.386116, type 2 (EV_REL), code 0 (REL_X), value 1
Event: time 1524816296.386116, -------------- SYN_REPORT ------------
Event: time 1524816296.475247, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
Event: time 1524816296.475247, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0
Event: time 1524816296.475247, -------------- SYN_REPORT ------------
Event: time 1524816296.542649, type 2 (EV_REL), code 0 (REL_X), value -1
Event: time 1524816296.542649, -------------- SYN_REPORT ------------
Event: time 1524816296.553777, type 2 (EV_REL), code 0 (REL_X), value -1
Event: time 1524816296.553777, -------------- SYN_REPORT ------------
Event: time 1524816296.598750, type 2 (EV_REL), code 0 (REL_X), value -1
Event: time 1524816296.598750, -------------- SYN_REPORT ------------
Event: time 1524816299.102308, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90002
Event: time 1524816299.102308, type 1 (EV_KEY), code 273 (BTN_RIGHT), value 1
Event: time 1524816299.102308, -------------- SYN_REPORT ------------
Event: time 1524816299.130065, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90002
Event: time 1524816299.130065, type 1 (EV_KEY), code 273 (BTN_RIGHT), value 0
Event: time 1524816299.130065, -------------- SYN_REPORT ------------
Event: time 1524816299.197529, type 2 (EV_REL), code 1 (REL_Y), value 1
Event: time 1524816299.197529, -------------- SYN_REPORT ------------
Event: time 1524816308.281969, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
Event: time 1524816308.281969, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1
Event: time 1524816308.281969, -------------- SYN_REPORT ------------
Event: time 1524816308.281994, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
Event: time 1524816308.281994, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0
Event: time 1524816308.281994, -------------- SYN_REPORT ------------
Event: time 1524816308.298937, type 2 (EV_REL), code 0 (REL_X), value -2
Event: time 1524816308.298937, -------------- SYN_REPORT ------------
Event: time 1524816308.321352, type 2 (EV_REL), code 0 (REL_X), value -1
Event: time 1524816308.321352, -------------- SYN_REPORT ------------
```

Hope one of you has a hint.

And BTW: I'm well aware of:
[Magic-Mouse2 Scrolling not working]("https://askubuntu.com/questions/945741/apple-magic-mouse-2-scrolling-not-working?rq=1")

Later today I'll test: [Install Kivy for MagicMouse MultiTouch]("https://askubuntu.com/questions/879799/in-ubuntu-16-10-multitouch-on-apple-magic-mouse-2-is-useless?rq=1") and [/etc/modprobe.d/magicmouse.conf Options]("https://askubuntu.com/questions/112454/disabling-middle-button-on-apple-magic-mouse")

---

### Post by mircsicz on 2018-04-27
Bump

---

