---
title: "Touchpad tapping trouble"
date: 2008-06-24
forum: Hardware
---

### Post by JamesBonz on 2008-06-24
Alright, well long story short. I haven't touched Ubuntu since Dapper on my older laptop and could never get wireless working making running Ubuntu useless. I recently got a new laptop and decided to dual boot Vista and the newest possible version (Hardy). It works great, I love it just the touchpad tap-to-click is driving me absolutely crazy its so bloody sensitive. I've searched and search and nothing helps. It seems to be a fairly average problem and most people fix it by adding    Option   "MaxTapTime"    "0", which does nothing, downloading gsynaptics and adding Option   SHMConfig   "true" (or "on" as works for a lot of people too) still nothing, I've tried a few more things and still nothing, I've read at least 20 links, and actually crashed Ubuntu a few times by screwing with the xorg too much. 

My laptop is an Acer Aspire 5920-6273.

Now one last thing, I'm quite the novice when it comes to Ubuntu/Linux so please add step by step instructions, since most things will go straight over my head.

If anyone have ANY advice I would be greatly appreciative.

~ Shawn.W.

---

### Post by danielph on 2008-06-24
This maybe a silly question but did you try running the application gsynaptics and changing the touchpad settings from there? You only mentioned installing it.

(Press ALT-F2 together and then type gsynaptics in dialog box)

---

### Post by JamesBonz on 2008-06-24
Oh yes definitely. No matter what I did (disable touchpad, or even just disable tapping) it would not work, I read this may be a problem if the touchpad was an alps made pad, but in this case it is not. Whats worse after the machine was restarted, or the xserver was with ctrl+alt+backspace the settings would be back to default, so even if this option did work, it would have to keep selecting disable tapping.

---

### Post by danielph on 2008-06-24
Try cleaning up your xorg.conf so no other options are picked up from here and then use gsynaptics to set the mouse.

---

### Post by JamesBonz on 2008-06-24
xorg is completely ...well... stock? only change that I have made is the adding the SHMConfig option to get gsynaptics past the initial error. After each failed attempt I restore xorg again, since a few failed attempts earlier, I went onto the next "fix" and I crashed ubuntu and had to reinstall.

---

### Post by danielph on 2008-06-24
I can only guess that xorg.conf is changing something. No harm taking a look. Can you post it here?

---

### Post by JamesBonz on 2008-06-24
No problem, here ya go.

[QUOTE=xorg]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
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
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection[/QUOTE]

---

### Post by danielph on 2008-06-24
Under the section Module try adding > Load            "synaptics"and maybe try removing >      Option        "HorizEdgeScroll"    "0"

You will need to restart X (Ctrl-Alt-Backspace) for changes to take effect

---

### Post by JamesBonz on 2008-06-24
Done & no change.
gsynaptics options still have no effect.

---

### Post by danielph on 2008-06-24
I just read [this page]("http://gsynaptics.sourceforge.jp/") and it says > To use your setting values at each starting of Xserver, you have to run gsynaptics-init at the starting of Xserver. 

If you are: 
Ubuntu GNOME users,
you have to add gsynaptics-init on [Applications] - [Desktop Preferences] - [Advanced] - [Sessions] - [Startup Programs ] in GNOME Menu

Not something I have done to get mine working, but I am out of ideas, so you may want to follow it. I have it working with Arch linux and KDEmod and Gnome with Ubuntu on another laptop. You are welcome to any of my config files. Good Luck

EDIT: Also check your X error logs at /var/log to see if there are any mention of synaptics. On my machine the log file is /var/log/Xorg.0.log so > cat /var/log/Xorg.0.log|grep synaptics

---

### Post by JamesBonz on 2008-06-24
I hate having to type this again :(

No go. That was already there, I removed the start-up session and readded it with that command, no change at all, gsynaptic settings still have no effect, and the ubuntu mouse control (with a 'touchpad' tab) also still has no effect.

---

### Post by danielph on 2008-06-24
Check the X log as above for clues and check that "xserver-xorg-input-synaptics" is installed.

Also for checking for errors: > cat /var/log/Xorg.0.log|grep EEand warnings > cat /var/log/Xorg.0.log|grep WW

---

### Post by Absolut Newbee on 2008-07-18
I have the same problems with the touch pad tapping, it turns out that the Aspire 5920 series is not compatible with Gsynapatics see ([http://w1.894.telia.com/~u89404340/touchpad/compatibility.txt](http://w1.894.telia.com/~u89404340/touchpad/compatibility.txt)) for more details

Hope you have fund an other way

---

### Post by errenay on 2008-07-19
This may help you:
[http://ubuntuforums.org/showthread.php?t=517156]("http://ubuntuforums.org/showthread.php?t=517156")

---

### Post by Absolut Newbee on 2008-07-21
Thanks for the link, got everything to work

---

