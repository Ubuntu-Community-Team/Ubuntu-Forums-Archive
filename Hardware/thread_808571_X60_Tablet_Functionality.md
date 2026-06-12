---
title: "X60 Tablet Functionality"
date: 2008-05-26
forum: Hardware
---

### Post by Nubnut on 2008-05-26
I've installed 8.04 on a Lenovo IBM Thinkpad X60. I've searched the forums and can see that many users have installed on this system and got the Tablet functionality working but I haven't been able to find a "How to". So far I've downloaded and installed wacom-tools and xserver-xorg-input-wacom through synaptic but dont know what to do next.

I've searched extensively but cannot find a guide that explains how to enable tablet touchscreen, pen, etc.
Can anyone help or point me to a fairly basic guide.

---

### Post by Nubnut on 2008-05-26
I've since found the following guide and am following it...

[http://luke.no-ip.org/x60tablet/edgy.html](http://luke.no-ip.org/x60tablet/edgy.html)

---

### Post by lklk on 2008-05-26
You have to add this to the file /etc/X11/xorg.conf. You need root privileges to edit it, the easiest way is to type "sudo gedit /etc/X11/xorg.conf" into the terminal without the quotes.

#####
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
#####

Next you have to edit this section of the same file

######
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
######

to look like this.

#####
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
######

Now all you have to do is Log out and Log in again or just hit Alt-Ctrl-Backspace which will restart the Xserver and log you out. I'm trying to figure out how to get the right click, middle click, and left click on my x61 stylus.

Sorry if I told you things you might have known. If my method doesn't work make sure you search for wacom in synaptic and install all the results, 2 if I recall, and restart the Xserver. If that doesn't work try this thread [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915) but when I tried it that way it work for ten seconds then X restarted and it didn't work again.

---

### Post by Nubnut on 2008-05-27
Thanks lklk, I followed your instructions but unfortunately it hasn't worked. Perhaps I've overlooked something in my editing of xorg.conf.
I've installed both wacom-tools and xserver-xorg-input-wacom through synaptic...

Here's my xorg.conf if anyone can help:...
```

Section "InputDevice"
	Driver 		"wacom"
	Identifier 	"stylus"
	Option 		"Device" 	"/dev/input/wacom"
	Option 		"Type" 		"stylus"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection

Section "InputDevice"
	Driver 		"wacom"
	Identifier 	"eraser"
	Option 		"Device" 	"/dev/input/wacom"
	Option 		"Type" 		"eraser"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection

Section "InputDevice"
	Driver 		"wacom"
	Identifier 	"cursor"
	Option 		"Device" 	"/dev/input/wacom"
	Option 		"Type" 		"cursor"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection

Section "InputDevice"
	Driver 		"wacom"
	Identifier 	"pad"
	Option 		"Device" 	"/dev/input/wacom"
	Option 		"Type" 		"pad"
	Option 		"USB" 	"on"
EndSection

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
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice 	"Synaptics Touchpad"
	InputDevice 	"stylus" "SendCoreEvents"
	InputDevice 	"cursor" "SendCoreEvents"
	InputDevice 	"eraser" "SendCoreEvents"
	InputDevice 	"pad"
EndSection
```

---

### Post by buntumaddy on 2008-10-22
Just wanted to say quick thanks to lklk for that nice detailed post. Got my stylus working and moving the cursor around. Left clicks are fine as well. But the right clicks do not work yet. Is there a solution yet?

---

### Post by sarah.fauzia on 2008-10-27
You need to remap the right-click button. Right now, it's directing to a button that isn't the real "right-click" on your pen; for my X61T, I add, in the stylus section of my xorg.conf:

```
  Option          "Button2" "3"
```

So, as you see, button 2 is remapped to button 3, which (should, since I have a similar model tablet) correspond to the right-click.

Ubuntu has amazing tablet PC support and overall computer support, with Intrepid Ibex. Two software you must try--easystroke and xournal. Xournal has a nifty ruler tool, which is important if you draw graphs, and can't be found in Windows Journal *or* OneNote (I've used both). And EasyStroke beats the socks of Vista's pen flicks. Oh, and cellwriter, a program which allows handwriting recognition input; here's a trick: if you want easy access to cellwriter when you're web-browsing, make a gesture with easystroke and enter the command as "cellwriter --show-window" (without quotes). Then, to hide cellwriter, make a gesture with the command "cellwriter --hide-window".

You can install Xournal and Cellwriter easily by searching for them specifically in Synaptic Package Manager, and Easystroke by adding "deb [http://ppa.launchpad.net/thjaeger/ubuntu](http://ppa.launchpad.net/thjaeger/ubuntu) intrepid main" (without quotes) to your Sources List (open Synaptic > Settings > Repositories > Third Party Software > Add)

I hope this helps! :) Good luck with using your tablet in Ubuntu! For your touchscreen, google the _thinkwiki_; they have a guide on how to make that work (along with many other things). To calibrate my touchscreen I had to install Java first (it isn't specified in the guide), so go to Applications > Add/Remove > Change Show to "All available applications" > Install Sun Java 6 Runtime. Then try the calibration tool (you'll see in the guide, it's called wacomcpl). To get it to work, you're going to need the latest wacom drivers...and they're going to tell you to remove your current ones. Don't worry, you get it back after you reinstall them, but the way they tell you to. It isn't hard--it worked for me! :)

---

### Post by sarah.fauzia on 2008-10-27
Sorry, made a duplicate post accidentally.

---

