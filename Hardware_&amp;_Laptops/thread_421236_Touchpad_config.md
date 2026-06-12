---
title: "Touchpad config"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by poetofzwan on 2007-04-24
Hey everyone,

I am a very new ubuntu user and im finding the OS fairly good at the moment.  I managed to install ubuntu as second OS/use Automatrix, install photoshop etc fine, but I have one slight complaint.  My touchpad is too sensitive.  I keep clicking links by mistake.  I looked in ¨system" ---> ¨preferences¨ ----> ¨mouse¨ but it doesnt seem to have any way of disabling clicking with mousepad.  Can this be done?

I am using Ubuntu Feisty Fawn.  It would be great to find how to change the setting rather than have to use a mouse.

Michael

---

### Post by strabes on 2007-04-24
You want to completely disable tap-to-click? It's easy. You just have to add one line to the Synaptics Touchpad section of your /etc/X11/xorg.conf.

First edit that file:
```
gksudo gedit /etc/X11/xorg.conf
```

Next find the Synaptics Touchpad Section. It will look something like this:
> Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
EndSection

Simply add the following line before "EndSection" just like the other options:
> Option      "MaxTapTime" "0"

Save the file (Ctrl+S) and restart your X server by hitting Ctrl+Alt+Backspace, and tap-to-click should be disabled.

---

### Post by poetofzwan on 2007-04-24
Thanks for the reply, but I seem to have a problem.  I seem to not have anything similar to the ¨input device" that you mention.  This is what I have,

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
```

They seem to be for wacom tablet and a normal mouse, both of which I do not have connected.  Can I simply add in your other lines of code?

---

### Post by strabes on 2007-04-24
The "wacom" sections you can just delete out of there since you don't have a tablet PC. You could try to just add the lines that I posted, I'm doubtful as to whether it will work or not though. If you decide to add them into your xorg.conf, you should make a backup of your xorg.conf in case something breaks:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now add the lines I mentioned in my previous post into the xorg.conf.

You will also need to add this line into the "ServerLayout" section of the xorg.conf: >         InputDevice    "Synaptics Touchpad"

When you restart your X server with ctrl+alt+backspace, if it doesn't work, hit ctrl+alt+F1, and run this command to restore your old xorg.conf:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by poetofzwan on 2007-04-25
Thanks strabes, that worked like a treat.  Things feel much better now.

Can I just ask, as i trying to learn, what is xorg?  Is it just a system that ubuntu uses to manage hardware?

---

### Post by strabes on 2007-04-27
"xorg" = [www.x.org](www.x.org) ... [www.x.org](www.x.org)

---

### Post by anemptygun on 2007-10-10
thanks for the info.

---

### Post by _Silhouette_ on 2008-04-13
Oh thanks so much! I couldn´t stand the touchpad before, but now its disabled, just like I wanted! Thanks again!

---

