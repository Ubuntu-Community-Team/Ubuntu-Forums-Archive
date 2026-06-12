---
title: "Touchpad not working after login with specific account"
date: 2016-10-21
forum: Hardware
---

### Post by alejomj on 2016-10-21
Hi, my touchpad stops working just when I login, also with guess account it's working fine but when I login with my account it stops. 


~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                   	id=14	[slave  keyboard (3)]

The command for enable xinput enable 11 or xinput --set-prop 11  "Device Enabled" does work.

Also I follow this:
[h=2]Touchpad not working after login[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]This usually happens when you disable your touchpad and then suspend your computer. To fix this just run this command:[FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
and no luck.

additional info:

xinput -list-props 11
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
	Device Enabled (116):	0
	Coordinate Transformation Matrix (118):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (241):	1
	Device Accel Constant Deceleration (242):	2.500000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	12.500000
	Synaptics Edges (245):	614, 3481, 307, 1740
	Synaptics Finger (246):	25, 30, 0
	Synaptics Tap Time (247):	180
	Synaptics Tap Move (248):	201
	Synaptics Tap Durations (249):	180, 100, 100
	Synaptics ClickPad (250):	0
	Synaptics Middle Button Timeout (251):	75
	Synaptics Two-Finger Pressure (252):	282
	Synaptics Two-Finger Width (253):	7
	Synaptics Scrolling Distance (254):	-91, -91
	Synaptics Edge Scrolling (255):	0, 0, 0
	Synaptics Two-Finger Scrolling (256):	1, 1
	Synaptics Move Speed (257):	1.000000, 1.750000, 0.043687, 0.000000
	Synaptics Off (258):	2
	Synaptics Locked Drags (259):	0
	Synaptics Locked Drags Timeout (260):	5000
	Synaptics Tap Action (261):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (262):	1, 1, 0
	Synaptics Circular Scrolling (263):	0
	Synaptics Circular Scrolling Distance (264):	0.100000
	Synaptics Circular Scrolling Trigger (265):	0
	Synaptics Circular Pad (266):	0
	Synaptics Palm Detection (267):	0
	Synaptics Palm Dimensions (268):	10, 200
	Synaptics Coasting Speed (269):	20.000000, 50.000000
	Synaptics Pressure Motion (270):	30, 160
	Synaptics Pressure Motion Factor (271):	1.000000, 1.000000
	Synaptics Resolution Detect (272):	1
	Synaptics Grab Event Device (273):	0
	Synaptics Gestures (274):	1
	Synaptics Capabilities (275):	1, 1, 1, 1, 1, 0, 0
	Synaptics Pad Resolution (276):	38, 40
	Synaptics Area (277):	0, 0, 0, 0
	Synaptics Noise Cancellation (278):	22, 22
	Device Product ID (236):	2, 8
	Device Node (237):	"/dev/input/event6"

cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0008 Version=0700
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input15
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=1
B: EV=b
B: KEY=e520 70000 0 0 0 0
B: ABS=260800000000003

I will appreciate your help, 

thx in advance.

---

### Post by vanili on 2016-10-25
It feels that I had a similar issue. Touchpad itself was different in my case 

```
I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003

```

but its behavior was quite similar. I've solved this modifying touchpad setting from Advanced to Basic in BIOS. Not sure if it is the best solution, but it works for me...

---

