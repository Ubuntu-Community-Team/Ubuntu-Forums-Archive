---
title: "Turning Off Synaptic Touchpad Taping?"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by DocHolliday2006 on 2007-05-27
I need to turn off taping on my Synaptic Touchpad laptop.

I found a bunch of articles telling me how to disable this using a file called xorg.conf, but my mouse is not listed.

All I have in there is 
Section "input device"
Identifier" Configured Mouse"
Driver "Mouse"

IS that what I need to be dealing with?  Is there a driver I can get that will make it recognize the pad as a synaptic? 

What exactly do I need to do?

Also, when I try to save changes to Xorg.conf, it tells me I don't have access, but I'm using the only account on the OS, and I didn't disable any privledges. Usually it just asks me for my password. How do I get around that?

---

### Post by reacocard on 2007-05-27
> **DocHolliday2006 said:**
> I need to turn off taping on my Synaptic Touchpad laptop.

I found a bunch of articles telling me how to disable this using a file called xorg.conf, but my mouse is not listed.

All I have in there is 
Section "input device"
Identifier" Configured Mouse"
Driver "Mouse"

IS that what I need to be dealing with?  Is there a driver I can get that will make it recognize the pad as a synaptic? 

What exactly do I need to do?

Also, when I try to save changes to Xorg.conf, it tells me I don't have access, but I'm using the only account on the OS, and I didn't disable any privledges. Usually it just asks me for my password. How do I get around that?

The section you're looking for should start like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
```

To edit the file, you need to use sudo to gain root privileges. Press alt+f2 and enter this:
```
gksudo gedit /etc/X11/xorg.conf
```

Be very careful when editing the xorg.conf, if you mistype it could cause your GUI to not start. You migth want to save a backup of the xorg.conf before editing it.

---

### Post by ugm6hr on 2007-05-27
I suspect you have not installed the Synaptic driver at all.  If the xorg.conf doesn't contain the references as stated above - it's not installed.  The only way to turn off tapping is to add those entries manually to xorg.conf, and then turn tapping off.  While you're there, you can activate scrolling etc if you want.

The bits you need to add (in the correct sections) are:

Section "Module"
	**Load	"synaptics"**
EndSection

[B]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection
[/B]

Section "ServerLayout"
	**InputDevice	"Synaptics Touchpad"**
EndSection

Unfortunately, I just can't remember exactly what the Tap Off command in Section InputDevice is!  Just search in these forums - it's something like *Option TapDelay 0*

---

### Post by DocHolliday2006 on 2007-05-27
> **reacocard said:**
> The section you're looking for should start like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
```


This is not in the xorg.conf file. All I have for input devices are the generic mouse and keyboard.



To edit the file, you need to use sudo to gain root privileges. Press alt+f2 and enter this:
```
gksudo gedit /etc/X11/xorg.conf
```

Be very careful when editing the xorg.conf, if you mistype it could cause your GUI to not start. You migth want to save a backup of the xorg.conf before editing it.[/QUOTE]

---

### Post by Ateo on 2007-05-27
Install gsynaptics (gnome) or ksynaptics (kde) and you will have many options for your touchpad. Then, your inputdevice section should look something like:```
Section "InputDevice"
    # Required packages:
    # libsynaptics and ksynaptics (or gsynaptics Gnome)
    Identifier  "Mouse0"
    Driver      "synaptics"
    Option      "SHMConfig" "true"
    Option      "Protocol" "auto-dev"
    Option      "Device" "/dev/input/event1"
EndSection
```

---

### Post by kerry_s on 2007-05-27
i use qsynaptics->

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"	"true"

EndSection

```

---

### Post by DocHolliday2006 on 2007-05-27
Not working. I installed Qsynaptics. When I try to open the program, it tells me that I must set SHMConfig to true in xorg.conf. I open up xorg.conf and there is no shmconfig. There is also no Synaptics touchpad, only generic keyboard, and configured mouse, and wacom for input devices.

What should I do?

> **kerry_s said:**
> i use qsynaptics->

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"	"true"

EndSection

```

---

### Post by kerry_s on 2007-05-27
Run this in terminal-> sudo dpkg-reconfigure -phigh xserver-xorg
that will give the synaptics section
use> gksu gedit /etc/X11/xorg.conf
to access xorg.conf
then just add the line to that section-> Option		"SHMConfig"	"true"
then restart X with> ctrl + alt + backspace

Also you need to add> qsynaptics -r
to your startup apps so it restores the settings on startup.

---

### Post by ugm6hr on 2007-05-27
> **DocHolliday2006 said:**
> Not working. I installed Qsynaptics. When I try to open the program, it tells me that I must set SHMConfig to true in xorg.conf. I open up xorg.conf and there is no shmconfig. There is also no Synaptics touchpad, only generic keyboard, and configured mouse, and wacom for input devices.

What should I do?

Try manually editing xorg.conf to add the necessary bits, as I listed above, then reboot.  Qsynaptics (or whatever you want to use) will then work.

---

### Post by kerry_s on 2007-06-01
Okay, here's the setup to disable tapping but keep the scroll and toucpad movement. Also pessing both buttons at the same time gives you middle click.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option             "SHMConfig" "on"
	Option		"HorizScrollDelta"	"0"
        Option              "RBCornerButton"    "2"
        Option              "LBCornerButton"    "0"
        Option              "LTCornerButton"    "0"
        Option              "RTCornerButton"    "0"
        Option              "EmulateMidButtonTime" "100"
        Option              "MaxTapTime" "0"
        Option              "EdgeMotionMinSpeed" "30"
        Option              "EdgeMotionMaxSpeed" "50"
EndSection

```

---

