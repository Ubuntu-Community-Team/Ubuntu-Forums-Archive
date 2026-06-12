---
title: "touchscreen - mouse drags on tap"
date: 2011-01-30
forum: Hardware
---

### Post by naugtur on 2011-01-30
Hi. I did search this, but I haven't found anybody mentioning this problem.

My touchscreen is the one in Dell Lattitude 2100 and I'm using xubuntu 10.04, but it worked out of the box, so I expect this issue can be related to other flavours of ubuntu too.
Hi. I did search this, but I haven't found anybody mentioning this problem.

My touchscreen is the one in Dell Lattitude 2100 and I'm using xubuntu 10.04, but it worked out of the box, so I expect this issue can be related to other flavours of ubuntu too.

When I touch a screen the mouse action is (often, not always) first to click and then - move to the spot I touched. This results in a drag.
To illustrate this I attach an image from gimp where I tried to draw some dots (and dots only)

[IMG]http://jquerymobiledictionary.dyndns.org/pub/probl.jpg[/IMG]

I would like to be able to scribble on my touchscreen. Where can I fix that?

xinput list --long

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
	Reporting 3 classes:
		Class originated from: 14
		Buttons supported: 12
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
		Button state:
		Class originated from: 14
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 1472.000000 - 5472.000000
		  Resolution: 76000 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 1408.000000 - 4448.000000
		  Resolution: 117000 units/m
		  Mode: relative

&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 4
		Buttons supported: 10
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None
		Button state:
		Class originated from: 4
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 4
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative

&#9116;   &#8627; IDEACOM  IDC 6680                       	id=11	[slave  pointer  (2)]
	Reporting 6 classes:
		Class originated from: 11
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 11
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2861.000000
		Class originated from: 11
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 4027.000000
		Class originated from: 11
		Detail for Valuator 2:
		  Label: Abs Z
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 11
		Detail for Valuator 3:
		  Label: Abs Rotary X
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 11
		Detail for Valuator 4:
		  Label: Abs Pressure
		  Range: 0.000000 - 1.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000

&#9116;   &#8627; IDEACOM  IDC 6680                       	id=12	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 12
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 12
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 65534.000000
		Class originated from: 12
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 22911.000000

&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 14
		Buttons supported: 12
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
		Button state:
		Class originated from: 14
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 1472.000000 - 5472.000000
		  Resolution: 76000 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 1408.000000 - 4448.000000
		  Resolution: 117000 units/m
		  Mode: relative

&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 16
		Buttons supported: 5
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 16
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 16
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
	Reporting 1 classes:
		Class originated from: 13
		Keycodes supported: 248

    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 5
		Keycodes supported: 248

    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 6
		Keycodes supported: 248

    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 7
		Keycodes supported: 248

    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 8
		Keycodes supported: 248

    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 9
		Keycodes supported: 248

    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 13
		Keycodes supported: 248

    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 15
		Keycodes supported: 248

```

Edit:

I also found this bug report: [https://bugs.launchpad.net/ubuntu/+bug/573006](https://bugs.launchpad.net/ubuntu/+bug/573006)

---

