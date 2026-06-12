---
title: "touchpad not detected"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2008-01-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131362](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131362) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My touchpad is [not detected at boot]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131362"). Feisty has been equally blind to this essential piece of hardware, so I'm becoming slightly suspicious about Hardy making any difference. It seems to have to do with recent kernels, since PCLinuxOS detects it just fine (kernel 2.6.18?). 
That's just fine, new features, new bugs right? But two rounds of new kernels and still no change? Is there some chance I can get it working again? Or will Hardy be any better?

The touchpad is not shown in /proc/bus/devices, so no surprise that Xorg tries to load the synaptics driver and fails to find a proper device. What could be changed in the kernel that make 2.6.18 see it without problems, en 2.6.20+ don't. 

I've tried the Fn+F7, checked my BIOS for any emulation options active, I've put psmouse as module in /etc/modules, but nothing helps.

---

### Post by jackflap on 2008-01-14
I'm not really sure I can help that much with your problem in particular, but one thing I am interested in is being able to test older kernels on newer systems. A couple of times, I've really wished I could roll-back to an older kernel easily from a newer installation.

One thing you could try, is get a hold of an Ubuntu 6.10 Live CD and boot it up just to test with. It runs the 2.6.17 kernel, and if they touchpad works, then you know they've broken it in a later release and haven't fixed it.

I'm not sure it's really that useful, but I suppose it would help you narrow down where to submit a bug for this issue. Also, kernel developers fix things that worked at one point in the past far more quickly than they implement new features, so, once the bug is submitted, it shouldnt be long.

Alex

---

### Post by DFreeze on 2008-01-14
I just did 'sudo tpconfig' and it said:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

What makes that tpconfig can find the touchpad in a linux distro that can't...

---

### Post by rocko_mtv on 2008-01-14
DFreeze,  is your touchpad _ completely_ in-op?   Does your touchpad GUI work? 

I am running  Ubuntu 7.04 Fiesty  and had problems getting the Touchpad GUI to open so I could disable the "tap click" function as the pad would not shut off during typing.  It was a typing nightmare.   I just got it working within the last two days and the solution was slightly  different than most of those I found in these forums.  The related threads here did help me solve my  TP issue but I had to tweak my  xorg.conf  some for my Toshiba Laptop.   My touchpad would not show up in xorg.conf at all but my pad had action.

If you think it would be helpful,  I would be happy to paste my xorg.conf ?

Let me know,
Rick

---

### Post by DFreeze on 2008-01-15
Hey Rick, thanks for offering assistance. My TP is completely dead. Not even a mention of it in /proc/bus/input/devices:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1241 Product=1177 Version=0110
N: Name="HID 1241:1177"
P: Phys=usb-0000:00:1c.0-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=event6 
B: EV=21
B: SW=1

```

But the strange thing is: I never did something with my xorg.conf until now, and xorg.conf lists some mouse as SynPS/2, which fits the description of my TouchPad. 

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"

```

but the USB mouse (when plugged in) is connected to /dev/psaux, and /dev/input/mice does nothing (when doing a 'sudo cat /dev/input/mice' and moving my finger on the TP or wiggling the mouse).

It always annoys me that I just don't know enough of the inner workings to trace back what is going on. But luckily there are these forums, where many smarter people offer their help ;)

---

### Post by Yellow Pasque on 2008-01-15
You're sure this isn't it?
> I: Bus=0003 Vendor=1241 Product=1177 Version=0110
N: Name="HID 1241:1177"
P: Phys=usb-0000:00:1c.0-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

---

### Post by DFreeze on 2008-01-15
To be honest, I copy-pasted the devices list from my bugreport, which is a bit dated already. In the meanwhile I installed the 64bit edition of Ubuntu, so maybe the listing has changed. In my bugreport I also mention that PCLinuxOS lists it as connected to the ISA bus, and your suggestion finds something in the USB port, am I right? I'm a total nitwit when it comes to protocols and layers, so maybe I'm missing something here.

Anyway, I'll post my current devices list tonight, to see if something has changed. Thanks for listening, so far!

---

### Post by rocko_mtv on 2008-01-15
See if there is anything in this that may help?  SHMConfig had to be "true" not "On" for mine to work and I had to put  load "synaptics"  in my module  section.  I uncommented  (#) the "CorePointer" in the second mouse input section. Not sure if it makes a difference with "AlwaysCore" in the Touchpad section but it works so I did not change it.   It may if I use a regular mouse ever?

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load 	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver 		"synaptics"
	Option 		"AlwaysCore"
	Option 		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"LeftEdge" "1700"
	Option 		"RightEdge" "5300"
	Option 		"TopEdge" "1700"
	Option 		"BottomEdge" "4200"
	Option 		"FingerLow" "25"
	Option 		"FingerHigh" "30"
	Option 		"MaxTapTime" "0"
	Option 		"MaxTapMove" "220"
	Option 		"VertScrollDelta" "100"
	Option 		"MinSpeed" "0.06"
	Option 		"MaxSpeed" "0.12"
	Option 		"AccelFactor" "0.0010"
	Option 		"SHMConfig" "true"
EndSection

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
#	Option 		"CorePointer"
	Option 		"Device" "/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"Emulate3Buttons" "true"
EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
_____________________________________________________________________________

---

### Post by DFreeze on 2008-01-17
Hey, thanks for your time! I really appreciate it. It's a little later than I wanted, but I checked my /proc/bus/input/devices once more. Once booted without the USB mouse, and once after I plugged it in. 

Here's what's in the file without the USB mouse:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=402000000 3802078f840d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=event5 
B: EV=21
B: SW=1

```

And this line was added when I plugged the USB mouse in.

```

I: Bus=0003 Vendor=1241 Product=1177 Version=0110
N: Name="HID 1241:1177"
P: Phys=usb-0000:00:1c.0-3/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

```

So, nothing indicating a TouchPad so far...

I'll come back on your suggestions for the xorg.conf file, haven't had time for those yet.

---

### Post by rocko_mtv on 2008-01-25
Any luck so far DFreeze?

---

### Post by DFreeze on 2008-01-28
Well, I just applied the relevant (to my insights) parts of your xorg.conf but no luck. Thanks anyway for helping me.  

I added Load Synaptics to the Modules section and "SHMConfig true" and Option "AlwaysCore" to my xorg.conf, but the touchpad doesn't work still. My Xorg.0.log gives this: 

```

(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "true"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

```

Any ideas left? ;-)

---

### Post by Elitist_Phoenix on 2008-02-18
Hey man did u get it working yet? I seem to have exactly the same problem as you.
The kernel doesn't seem to detect the touchpad. Yet the tpconfig does.

---

### Post by Elitist_Phoenix on 2008-03-02
Mate i just filed a bug report. Might want to add some of your details if u didn't get it working already. :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808)

---

### Post by DFreeze on 2008-03-03
> **Elitist_Phoenix said:**
> Mate i just filed a bug report. Might want to add some of your details if u didn't get it working already. :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808)

Hey Elitist_Phoenix, thanks for teaming up! I've already filed [a report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195009") as well, very much like the one I filed for Gutsy. Both are confirmed and of medium importance, but that's about as much reaction I've had.

You didn't have this with Gutsy?

---

### Post by Elitist_Phoenix on 2008-03-03
Only got the laptop recently so just decieded to install hardy straight onto it. On my old laptop in gusty the touchpad detected fine and it was another toshiba one. I'll add something onto the end of your bug report. Hopefully we can get this fixed by this release :D

---

### Post by DFreeze on 2008-03-03
Thanks for helping out. I'll do the same on your bugreport. It feels so annoying not to be able to do anything about it but complain. I'm not completely illiterate when it comes to computers and programming, but this is way out of my league. 

You could try some live-CD's of previous Ubuntu versions to see whether it is connected to kernel versions... I couldn't go further back than Feisty... Edgy didn't boot, so I couldn't check that. I used PCLinuxOS for that (kernel 2.6.18 ) and it found my touchpad without problems.

---

### Post by DFreeze on 2008-06-04
Finally! A fix is described in my [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195009"). My touchpad started working after adding "i8042.noloop=1" to the bootparameters. So, for everyone dealing with this issue, try this fix (or one of the others suggested in the bugreport).

---

### Post by kessaris on 2008-06-26
God Bless!!!

It works it works it works!!!!!!!!!!!!!!!!!!!!!!!!!

It took about three days, but thanks to this thread, it all came together.

Just for the record, it may also have something to do with i8042.nomux=1

I'm not going to experiment with any more of the settings, but sufficed to say you have saved a lot of trouble for me.

Best wishes, and thank you very much.  

Wait.. Let me scroll the window with the synaptics driver.
Ah.  Paradise.  Ubuntu!!!!!!!!!!!!

I have posted some instructions on adding the relevant options to the menu.lst file here [http://ubuntuforums.org/showthread.php?t=844968](http://ubuntuforums.org/showthread.php?t=844968)

Please let me know if there are any oversights or inaccuracies.

Best wishes,

Alexandros

---

