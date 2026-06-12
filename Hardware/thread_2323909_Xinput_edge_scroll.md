---
title: "Xinput edge scroll"
date: 2016-05-09
forum: Hardware
---

### Post by Imerion on 2016-05-09
I'm trying to configure my touchpad so the edge scrolls. I'm using the older hid_generic driver, so this was not a default setting and my system settings shows nothing related to this.
I heard libinput can't do edge scrolling, so I reverted to using xinput. My device has these options :

```
Device 'SYNAPTICS Synaptics HIDUSB TouchPad V03':
	Device Enabled (136):	1
	Coordinate Transformation Matrix (138):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (260):	0
	Device Accel Constant Deceleration (261):	1.000000
	Device Accel Adaptive Deceleration (262):	1.000000
	Device Accel Velocity Scaling (263):	10.000000
	Device Product ID (256):	1739, 32041
	Device Node (257):	"/dev/input/event15"
	Evdev Axis Inversion (264):	0, 0
	Evdev Axes Swap (266):	0
	Axis Labels (267):	"Rel X" (146), "Rel Y" (147)
	Button Labels (268):	"Button Left" (139), "Button Unknown" (259), "Button Right" (141), "Button Wheel Up" (142), "Button Wheel Down" (143)
	Evdev Scrolling Distance (269):	0, 0, 1
	Evdev Middle Button Emulation (270):	1
	Evdev Middle Button Timeout (271):	50
	Evdev Third Button Emulation (272):	0
	Evdev Third Button Emulation Timeout (273):	1000
	Evdev Third Button Emulation Button (274):	3
	Evdev Third Button Emulation Threshold (275):	20
	Evdev Wheel Emulation (276):	1
	Evdev Wheel Emulation Axes (277):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (278):	10
	Evdev Wheel Emulation Timeout (279):	200
	Evdev Wheel Emulation Button (280):	4
	Evdev Drag Lock Buttons (281):	0

```

I would assume Wheel Emulation is what I am looking for, but no matter how I set those up I can't seem to get edge-scrolling to work. My device has 5 buttons, which I got from xinput get-button-map: 1, 2, 3, 4 ,5.

---

### Post by vasa1 on 2016-05-10
Do you get any output by running **synclient** in a terminal? If you do, what do you see with **synclient | grep -i edgescroll**?

---

### Post by Imerion on 2016-05-11
Thanks for taking time to answer!

**synclient** gives me :

> Couldn't find synaptics properties. No synaptics driver loaded?

---

### Post by vasa1 on 2016-05-11
I don't follow GNOME developments but maybe you need to install `xserver-xorg-input-synaptics` if you stopped using `libinput`?

Before doing anything, you may want to search the pages [in this thread]("https://bbs.archlinux.org/viewtopic.php?id=210815") for `libinput` or `synaptics`. Here's one: [https://bbs.archlinux.org/viewtopic.php?pid=1618732#p1618732](https://bbs.archlinux.org/viewtopic.php?pid=1618732#p1618732)

---

### Post by Imerion on 2016-05-14
`xserver-xorg-input-synaptics` is installed, but I will check out that thread. Thanks for the tip!

---

