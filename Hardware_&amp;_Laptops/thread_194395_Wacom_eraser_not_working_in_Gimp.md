---
title: "Wacom eraser not working in Gimp"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by gwi on 2006-06-11
I have a Wacom Graphire 1 (type ET-0405-U). In Gimp the pen is working allright, incl. pressure sensitivity. But the eraser is not doing anything, not even moving the mouse pointer. The Wacom mouse is moving the pointer, but when I try drawing with it (by moving it while keeping the left button pressed), nothing is drawn.

I have setup the extended devices (cursor, eraser and stylus set to screen).
The relevant part of my xorg.conf is below.

I searched the forums, but could not find a solution to this problem. Any ideas what I can do to get the eraser (and the mouse) to work in Gimp? I am using the 64-bit version of Dapper on an AMD64.

```
Section "InputDevice"
Driver "wacom"
Identifier "Wacom_Cursor"
Option "Device" "/dev/input/event2"
Option "InputFashion" "Tablet"
Option "Mode" "Relative"
Option "Name" "GRAPHIRE / INTUOS (USB)"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "cursor"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "Wacom_Stylus"
Option "Device" "/dev/input/event2"
Option "InputFashion" "Pen"
Option "Mode" "Absolute"
Option "Name" "GRAPHIRE / INTUOS Stylus (USB)"
Option "Protocol" "Auto"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "stylus"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "Wacom_Eraser"
Option "Device" "/dev/input/event2"
Option "InputFashion" "Eraser"
Option "Mode" "Absolute"
Option "Name" "GRAPHIRE / INTUOS Eraser (USB)"
Option "Protocol" "Auto"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "eraser"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "Wacom_Stylus" "SendCoreEvents"
	InputDevice     "Wacom_Cursor" "SendCoreEvents"
	InputDevice     "Wacom_Eraser" "SendCoreEvents"
EndSection
```

---

### Post by gwi on 2006-06-14
Well, I solved part of my problem: switching the buttons by adding Option "Button2" "3" and Option "Button3" "2".

I still have no idea why Gimp won't recognise the mouse and eraser. The eraser is doing nothing in X at all. The mouse is working in X.

Anyone with ideas to solve the remaining problem?

---

### Post by chadk on 2006-06-15
Where did you add this?  I can't get my eraser working either.. -- can't get the pressure working for that matter.

---

### Post by graigsmith on 2006-06-15
here is my section, mine works perfectly, i have an intuos 2.
see i use the wacom device, you have to install "wacom-tools" to be able to use that.

```
Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Type" "cursor"
        Option "USB" "on"
        Option "Mode" "Relative"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Type" "stylus"
        Option "USB" "on"
        Option "PressCurve" "50,0,100,50"
        Option "Mode" "Absolute"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Type" "eraser"
        Option "USB" "on"
        Option "Mode" "Absolute"
EndSection

```

also you have to go into the gimp, preferences, configure extended input devices. change all of them to screen.

ps, the presscurve entry above is optional, makes the pen draw a little lighter, so that you have to press harder to get really dark lines.

chadk, you have to add it to your xorg.conf file.  there is a howto on wacom tablets. here
[http://ubuntuforums.org/showthread.php?t=25151&highlight=howto+wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=howto+wacom)

---

### Post by gwi on 2006-06-16
[QUOTE=chadk]Where did you add this?  I can't get my eraser working either.. -- can't get the pressure working for that matter.[/QUOTE]
I added it to the inputdevice section for the stylus, just among the other options that are already there.

---

### Post by gwi on 2006-06-16
[QUOTE=graigsmith]here is my section, mine works perfectly, i have an intuos 2.
see i use the wacom device, you have to install "wacom-tools" to be able to use that.[/QUOTE]
Tried that, doesn't solve the problem.

[QUOTE=graigsmith]also you have to go into the gimp, preferences, configure extended input devices. change all of them to screen.[/QUOTE]
I know, I already did that (should have told so, sorry).

Anyway, I can use the mouse now. I had to select a drawing tool with the mouse, because it is independent from the drawing tool selected with the stylus. I can't do that with the eraser, because with the eraser the mousepointer just doesn't move.

:? So the remaining problem is: why doesn't the mousepointer respond to movements with the eraser side of the pen (not just in Gimp, but anywhere in Gnome)?

---

