---
title: "[SOLVED] Syndaemon not running, but mouse disabled while typing?"
date: 2008-05-10
forum: Hardware
---

### Post by neunon on 2008-05-10
I'm having a rather strange problem and multiple Google searches haven't helped me.

I know it's possible to use syndaemon to ignore mouse input when the keyboard is being used. I do not have syndaemon running at all, but I'm still experiencing the effects of syndaemon.

To reproduce the problem easily, I can simply hold down the left or right arrow key in a Terminal window. While pressed, the mouse can't move. When I release the key, the mouse moves normally after about a half-second pause. I don't know what's causing this.

It's also affecting a game I'm developing, in which the arrow keys are used to move and the mouse is used to aim. So fixing this is pretty much essential.

I'm using a MacBook Pro, running Ubuntu 8.04.

Here's my xorg.conf:
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
    Identifier      "Synaptics Touchpad"
    Driver          "synaptics"
    Option          "SendCoreEvents"        "true"
    Option          "Device"                "/dev/psaux"
    Option          "Protocol"              "auto-dev"
    Option          "SHMConfig"             "on"
    Option          "LeftEdge"              "100"
    Option          "RightEdge"             "1100"
    Option          "TopEdge"               "50"
    Option          "BottomEdge"            "300"
    Option          "FingerLow"             "20"
    Option          "FingerHigh"            "30"
    Option          "MaxTapTime"            "180"
    Option          "MaxTapMove"            "20"
    Option          "FastTaps"              "0"
    Option          "VertScrollDelta"       "20"
    Option          "HorizScrollDelta"      "0"
    Option          "VertEdgeScroll"        "0"
    Option          "HorizEdgeScroll"       "0"
    Option          "VertTwoFingerScroll"   "1"
    Option          "HorizTwoFingerScroll"  "1"
    Option          "MinSpeed"              "0.59"
    Option          "MaxSpeed"              "0.78"
    Option          "AccelFactor"           "0.0015"
    Option          "RTCornerButton"        "0"
    Option          "RBCornerButton"        "0"
    Option          "LTCornerButton"        "0"
    Option          "LBCornerButton"        "0"
    Option          "TapButton1"            "1"
    Option          "TapButton2"            "3"
    Option          "TapButton3"            "2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"OpenGLOverlay" "on"
	Option 		"VideoOverlay" "on"
	Option		"UseFastTLS" "1"
	Option		"Capabilities" "0x00000800"
	Option		"EnablePrivateBackZ" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Any ideas?

---

### Post by Zorael on 2008-05-10
Could this be a hardware thing?

Regardless, I'd try to start syndaemon and setting the time to 0. Might disable it completely.

Else, I guess the only solution - which would confirm or deny whether it's a hardware thing - would be to change the driver from synaptic to mouse.

---

### Post by neunon on 2008-05-10
Well, it was worth a try. Syndaemon doesn't allow me to set a time of '0', it just prints out the command-line usage information.

Also tried using just the 'mouse' driver. Same problem... Any other ideas?

EDIT: Also just tried doing 'sudo dpkg-reconfigure -phigh xserver-xorg' to get a default xorg.conf. No effect as far as the strange problem goes... I guess xorg is not to blame.

---

### Post by neunon on 2008-05-10
Okay, sorry for the double-post, but I narrowed this down somewhat: The problem only occurs with a USB-connected mouse. It can be the Apple "Mighty Mouse" or it can be a Microsoft Intellimouse. Either way, it's only affecting USB mice. The Trackpad doesn't seem affected.

---

### Post by tageiru on 2008-05-11
I am experiencing the same issue on an intel imac. I tried a few different mouse drivers (mouse/evdev) but the problem persists.

Curiously the problem goes away if I use a live cd.

Copying the xorg.conf from the live environment did not help.

---

### Post by neunon on 2008-05-12
I wonder if it's a kernel boot parameter that makes the difference.

---

### Post by neunon on 2008-05-12
bump.

Seems there are no real differences in the boot parameters between the livecd and the kernel I've got installed.

Also, the problem has other symptoms as well. In apps using SDL for input, it's sometimes behaving as though there's a stuck key (the application believes the key is still down when it isn't). And I still can't use my USB mice with my machine if I type within a second of moving the mouse. It's very irritating for someone who moves as quickly as I do when using the computer...

Any ideas? This is really the only issue I'm having in Ubuntu right now, and it's also unfortunately making me consider switching to another distro (never had this problem in others). I'd hate to sacrifice such magical out-of-box functionality for a problem as annoying but trivial as this.

---

### Post by neunon on 2008-05-16
It turned out that 'mouseemu' was the cause of this. I reworded my Google searches and discovered _**[this open bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344")**_.

---

