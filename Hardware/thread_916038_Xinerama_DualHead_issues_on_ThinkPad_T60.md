---
title: "Xinerama DualHead issues on ThinkPad T60"
date: 2008-09-10
forum: Hardware
---

### Post by sarmstrong@serviceintel on 2008-09-10
Hi I am having problems getting a Xinerama DualHead (dual monitors) working on a new (to me) laptop computer. Here is what I know about my computer:

- IBM ThinkPad T60 Laptop
- Running the Ubuntu 8.04 Hardy Linux OS (2.6.24-19-generic)
- I have the Intel Integrated 945GM Graphics Card.
- I am trying to use Xinerama to do my dual head monitors support.
- I am trying to use the "xserver-xorg-video-i810" driver.
- My 2nd external monitor is a Dell E193FP (flat screen) 

I am NOT a Linux guru and I have so much more to learn with the OS. But I also know enough about the OS to get myself into trouble. :lolflag:

My dual monitor support is not working. But some interesting things are happening with it to make me think I am close to getting it working, that the Xinerama part of the "xorg.conf" file may be correct and that maybe I have some other underlying problem. 

My main laptop LCD works fine, and the 2nd external Dell monitor actually is set to the proper screen resolution based on my "xorg.conf" file settings. The mouse actually crosses the boundary between the two screens as if proper dual head support is working. But I am unable to drag a window from the main laptop monitor to the 2nd external Dell monitor and I am unable to right click and bring up the typical popup dialog in this 2nd external monitor. Finally the 2nd external Dell monitor is stuck in some grey'ish beige screen color. 

My "/var/log/Xorg.0.log" file does not appear to be complaining with any obvious error messages but:

- I can not access the "System/Preferences/Screen Resolution" dialog anymore due to an "The X Server does not support the XRandR extension" error message and when I first was given this laptop (before I mucked around with it) I was able to access this dialog.

plus 

- I am now unable to run XRandR commands like "xrandr -q" from a terminal window (not sure if I was ever able to run XRandR commands).

I have tried many combinations in my "xorg.conf" file and this morning I was thinking that maybe my problem was I was using "CRT,LFP" in my Device "MonitorLayout" option setting and that I needed to use "DFP,LFP". But the X server fails to start when I use "DFP". 

Here is my "xorg.conf" file:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
        Identifier      "Internal 945GM"
        Option          "DevicePresence" "true"
	Option		"MonitorLayout"	 "CRT,LFP" # tried DFP,LFP but X doesn't accept it on boot up
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "External 945GM"
        Option          "DevicePresence" "true"
	Option		"MonitorLayout"	 "CRT,LFP" # tried DFP,LFP but X doesn'taccept it on boot up
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
        HorizSync       30.0 - 83.0
        Vertrefresh     56.0 - 76.0
        Option          "Enable" "true"
        Option          "PreferredMode" "1024x768"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
        HorizSync       30.0 - 83.0
        Vertrefresh     56.0 - 76.0
        Option          "Enable" "true"
        Option          "PreferredMode" "1280x1024"
EndSection

Section "Screen"
        Identifier      "Internal"
        Monitor         "Internal Monitor"
        Device          "Internal 945GM"
        DefaultDepth    24
        SubSection      "Display"
            Depth       24
            Modes       "1024x768" "800x600" "640x480"
#            Virtual      1024 768
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External"
        Monitor         "External Monitor"
        Device          "External 945GM"
        DefaultDepth    24
        SubSection "Display"
            Depth       24
            Modes       "1280x1024" "1024x768" "800x600" "640x480"
#            Virtual      1280 1024
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier      "Default Layout"
        Screen 0        "Internal" 0 0
        Screen 1        "External" RightOf "Internal"
        Option          "Xinerama" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
	InputDevice     "Synaptics Touchpad"
EndSection

```

Any advice would be much appreciated.
Thxs in advance ... Steve

---

### Post by SneakyWho_am_i on 2009-04-01
I'm having great difficulty with this. Under Windows I had some trouble, and under Ubuntu I'm having trouble. Eventually, through sheer persistence, I got it working under Windows.

Not so much luck here. I'm doing battle with a(\n) HP 530 from Hewlett Packard. I don't recommend getting one, it's the most fragile and difficult laptop I've ever used.

But, this is not a laptop review. It's been what, six months since you posted this. Did you give up, like a normal person might and just settle for one screen? Are you still Linux-ing?

Now that I'm having this problem, I'm looking for answers. Your information helps, so thanks. If you've solved it, I'd love to know how.
If not, I'm keen to compare notes.

---

