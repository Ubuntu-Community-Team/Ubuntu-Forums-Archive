---
title: "Alps touchpad settings not saved after reboot.."
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by eitan_a on 2006-12-30
Hi guys.  I'm running Ubu 6.10 on a Sony Vaio laptop.  The device in mention is this..

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event5 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I have edited xorg.conf to configure the touchpad.  The necessary snippets from it..

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/input/mouse1"
	Option		"Device"		"/dev/input/event5"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"		"0.45"
	Option		"AccelFactor"		"0"
	Option		"MaxSpeed"		"1"
	Option		"RightEdge"		"900"
	Option		"TouchpadOff"		"0"
	Option		"GuestMouseOff"		"1"
	Option		"SHMConfig"		"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Synaptics Touchpad" "CorePointer"
#	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

My problem is that the touchpad settings do not take effect after a reboot, but they DO take effect after I log-out and log back in.  What is being loaded differently after a log-out / log-in compared to a reboot?  Is this a valid bug? 

Thanks!

---

### Post by eitan_a on 2006-12-30
Bump...still like help here..

running tpconfig gives me this..

Probing mouse port [/dev/psaux]
Could not open PS/2 Port [/dev/psaux]

---

### Post by eitan_a on 2006-12-31
won't anyone help me troubleshoot this problem???

I'm thinking there's a conflict between the PS/2 and touchpad settings.  On my laptop there is just my touchpad and nothing else.

---

### Post by tbranham on 2007-01-30
Well, I'm not going to be much help, because I'm having a similar problem. Let's see if another test-case will help shed some light on the solution...

I edited xorg, set my preferences with qsynaptics, applied them, and everything was peachy. Then I rebooted. Now I have to restart X (after the first login) and reload my preferences in qsynaptics every time I start the laptop to get the same functionality. Slightly annoying.

Here's the info:

From dmesg:
```

...
[17179716.852000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17179717.356000] psmouse.c: resync failed, issuing reconnect request
[17179718.088000] input: PS/2 Mouse as /class/input/input5
[17179718.108000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6

```

Here are the devices my lappy is reporting:
```

...
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
S: Sysfs=/class/input/input5
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event5 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```

Here's my xorg.conf:
```

...
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
...

```

And, finally, here's what tpconfig is saying:
```

eris% sudo tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

Hopefully this will help someone help us.

---

### Post by tbranham on 2007-02-03
Perhaps a little bump-ditty-bump bump is in order? 

I've started a methodical series of modifications to my xorg.conf, hoping that a simple change might do the trick. No luck yet. Anybody out there able to offer a suggestion?

---

### Post by jonobo on 2007-02-05
I can only help by verifying the problem - that really seems to be a bug.

For verification i removed all synaptics-relevant packages.

Then i reinstalled only "xserver-xorg-input-synaptics" in Version 0.14.6-0ubuntu3 .

Reboot.

Graphical Login to XServer - Desktop comes up - Touchpad is on, despite my xorg.conf, synclient-commands don't help.

Log-Off.

Login again.

Touchpad is off and obeys to synclient-commands.

This issue is driving me mad ):P 

Here are my systems specifications:

Amilo Pro V 2035 with ALPS Touchpad - Ubuntu 6.10 Edgy Eft.
```
jobo@zbox:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event5 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
```

Relevant Parts of my /etc/X11/xorg.conf
```
Section "ServerLayout"
	Identifier	    "Default Layout"
	Screen		    "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "InputDevice"
	Identifier     "Synaptics Touchpad"
	Driver		 "synaptics"	
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option         	"SHMConfig"	"on"
	Option		"TouchpadOff" "1"
EndSection
```

My synclient-Version:
```
jobo@zbox:~$ synclient -V
0.14.6
```

My Ubuntu-Version:
```
jobo@zbox:~$ uname -r
2.6.17-10-generic
```

Is this a bug or am i missing something ?

Any solutions ?

---

### Post by Michele84 on 2007-02-23
I have your same problem on a sony vaio vgn-c1s/h...everytime I need to log-out / log-in to turn on the scrollbar! Could be a driver problem? I mean...I have this tpuchpad:

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event3 ts1 
B: EV=f
B: KEY=420 70000 0 0 0 0
B: REL=3
B: ABS=1000003

but xorg.conf load Synaptics driver...is it ok???
>Thanks!!
Michele

---

### Post by cisforcojo on 2007-03-13
I have a similar problem. I want to help you narrow your problem.

For those of you using the "auto-dev" protocol for your touchpad in xorg.conf, check the X log 
and see what device event your touchpad is on and THEN check: /proc/bus/input/devices
to see what event your touchpad is REALLY on. I had a problem with 'auto-dev' not pointing to my touchpad correctly. NOW, I have /dev/input/event4 (or whatever) in my xorg.conf but i have to modify my xorg.conf every time I reboot to change it to the new event.

---

