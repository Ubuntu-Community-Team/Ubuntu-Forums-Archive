---
title: "Mouse acceleration settings not accessible with xinput"
date: 2015-06-04
forum: Hardware
---

### Post by darren24 on 2015-06-04
Hey all, first post.
I'm having an issue with my mice (generic wireless optical mouse bought from Rite Aid, Logitech Performance MX, and an older Logitech wired mouse with unknown model name) where xinput doesn't have any acceleration or sensitivity settings, and xset doesn't modify any mouse behavior.

What I've tried...
```
xset m 5 1
```
no result.
```
xset m 500 100
```
no result.
```
darren@darren-N73SV:/etc/X11$ xinput --list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=11	[slave  pointer  (2)]



```
which leads to...
```
darren@darren-N73SV:/etc/X11$ xinput --list-props 11Device 'Logitech USB-PS/2 Optical Mouse':
	Device Enabled (167):	1
	Coordinate Transformation Matrix (169):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Product ID (283):	1133, 49179
	Device Node (284):	"/dev/input/event5"
	Evdev Axis Inversion (297):	0, 0
	Evdev Axes Swap (299):	0
	Axis Labels (300):	"Rel X" (177), "Rel Y" (178), "Rel Vert Wheel" (292)
	Button Labels (301):	"Button Left" (170), "Button Middle" (171), "Button Right" (172), "Button Wheel Up" (173), "Button Wheel Down" (174), "Button Horiz Wheel Left" (175), "Button Horiz Wheel Right" (176), "Button Side" (288), "Button Extra" (289), "Button Forward" (607), "Button Unknown" (286), "Button Unknown" (286), "Button Unknown" (286), "Button Unknown" (286)
	Evdev Scrolling Distance (302):	1, 1, 1
	Evdev Middle Button Emulation (303):	0
	Evdev Middle Button Timeout (304):	50
	Evdev Third Button Emulation (305):	0
	Evdev Third Button Emulation Timeout (306):	1000
	Evdev Third Button Emulation Button (307):	3
	Evdev Third Button Emulation Threshold (308):	20
	Evdev Wheel Emulation (309):	0
	Evdev Wheel Emulation Axes (310):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (311):	10
	Evdev Wheel Emulation Timeout (312):	200
	Evdev Wheel Emulation Button (313):	4
	Evdev Drag Lock Buttons (314):	0

```

Every post I've come across says to change the "[COLOR=#111111][FONT=Consolas]Device Accel Constant Deceleration (267)[/FONT][/COLOR]" setting or some other acceleration profile or sensitivity setting, none of which exist for any of my mice. I've also tried messing with xorg.conf, but to no avail...I'm skeptical of this method though until i get some kind of useful output from xinput that can read any settings that look like they should control those settings.

What am i doing wrong? What can I do differently?

---

### Post by kryten35 on 2015-06-05
To get current values  for accel and threshold(sensitivity).
```
xset q | grep -A 1 Pointer

```

You  have to use  values like  2/1,3/1  etc to increase accel.  Or 1/2,1/3  to decrease accel
So
```
xset  m 2/1  4
```
sets accel to twice that of the default and sensitivity to 4.

I dont quite understand what you are trying to do though.Cant you adjust in your distros settings>hardware>mouse options?

---

### Post by darren24 on 2015-06-05
So using that command, I was able to see that "xset" was actually setting the "sensitvity" and "threshold" values for xset, but the problem is that none of my hardware seems to utilize what xset is setting (or xinput, or xorg.conf). Also, my "Mouse Pointer Speed" selection bar in settings doesn't have any affect on mouse speed either, so I'm stuck with whatever speed my mouse appears to provide natively. Again, each mouse hardware is different so each one provides a different speed. My older logitech wired is the slowest, the logitech performance MX is somewhere in the middle, and the generic wireless from rite aid is the fastest. What I don't understand is why I can't change any sensitivity settings for any of them. I have a feeling this might have something to do with nvidia drivers I installed for my graphics card somehow, because other than that its a pretty plain jane install. I installed gnome-flashback to get rid of the unity 3d stuff, but even if i go back to the regular unity desktop i still cant control mouse settings with any of the methods described.

---

### Post by kryten35 on 2015-06-05
Just did   xset m 4/1 4  and it worked fine with my logitech wireless usb mouse.
My output from  xinput list-props
```
xinput list-props  8
Device 'Logitech Anywhere MX':
    Device Enabled (151):    1
    Coordinate Transformation Matrix (153):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (281):    0
    Device Accel Constant Deceleration (282):    1.000000
    Device Accel Adaptive Deceleration (283):    1.000000
    Device Accel Velocity Scaling (284):    10.000000
    Device Product ID (270):    1133, 4119
    Device Node (271):    "/dev/input/event10"
    Evdev Axis Inversion (285):    0, 0
    Evdev Axes Swap (287):    0
    Axis Labels (288):    "Rel X" (161), "Rel Y" (162), "Rel Horiz Wheel" (279), "Rel Vert Wheel" (280)
    Button Labels (289):    "Button Left" (154), "Button Middle" (155), "Button Right" (156), "Button Wheel Up" (157), "Button Wheel Down" (158), "Button Horiz Wheel Left" (159), "Button Horiz Wheel Right" (160), "Button Side" (274), "Button Extra" (275), "Button Forward" (276), "Button Back" (277), "Button Task" (278), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273)
    Evdev Scrolling Distance (290):    1, 1, 1
    Evdev Middle Button Emulation (291):    0
    Evdev Middle Button Timeout (292):    50
    Evdev Third Button Emulation (293):    0
    Evdev Third Button Emulation Timeout (294):    1000
    Evdev Third Button Emulation Button (295):    3
    Evdev Third Button Emulation Threshold (296):    20
    Evdev Wheel Emulation (297):    0
    Evdev Wheel Emulation Axes (298):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (299):    10
    Evdev Wheel Emulation Timeout (300):    200
    Evdev Wheel Emulation Button (301):    4
    Evdev Drag Lock Buttons (302):    0
```

You will see that your posted output lacks any of the accel props  in my output.
    Device Accel Profile (281):    0
    Device Accel Constant Deceleration (282):    1.000000
    Device Accel Adaptive Deceleration (283):    1.000000
    Device Accel Velocity Scaling (284):    10.000000
So for me:
```
xinput --set-prop 8 'Device Accel Constant Deceleration' 2
```
doubles my mouse accel.

I think the problem is driver/hardware incompatibility.The props depend on mouse driver support in kernel.
What distro version and kernel are you running? I think if you update to a more recent version theres a good chance that
your problem might resolve.Updated kernel will have newer touchpad/mice drivers.

Im on ubuntu 15.04 mate 64 bit/ kernel is 3.19       If you try a live dvd image of 15.04 does your problem resolve?

---

### Post by darren24 on 2015-06-07
```
darren@darren-N73SV:~$ uname -a
Linux darren-N73SV 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
darren@darren-N73SV:~$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l
```

I find it hard to believe that 3.16 doesn't have support for this hardware...but i agree with your thought process. Something isn't getting picked up right by the kernel/drivers. the question is what, and why...

edit: i tried a livecd of systemrescuecd and i was able to set accel settings using xset m, but xinput isn't included in srcd so i couldn't check that. I'll try to debug more with 15.04 later...

---

