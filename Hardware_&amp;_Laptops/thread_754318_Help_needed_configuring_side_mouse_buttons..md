---
title: "Help needed configuring side mouse buttons."
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by NDX on 2008-04-13
I have tried various tutorials to configure the side buttons for my mouse, however I can not get it to work. The mouse is a Dynex 7 button mouse (2 side, 3 wheel, 2 click). I have tried the Driver "mouse" and "evdev" configurations. I am getting annoyed with the constant xorg failures and non-responding mouse after every trial and having to reload the backup. 

The actual Model No. is : DX-WMSE

My current working xorg.conf 
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
```

According to "cat /proc/bus/input/devices" I have (I do not know if this is helpful):
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

and this could be due to my previous trying-to-fix-it errors

```
I: Bus=0003 Vendor=0461 Product=4d42 Version=0111
N: Name="Dynex 5-Button Wired Optical Mouse"
P: Phys=usb-0000:00:10.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```

Please and thank-you. :confused:

---

### Post by broncavfan on 2008-06-08
I have the same mouse and I've spent too long trying to get it set up correctly, but I can safely say I've done just that.  Here's what I did.  I followed the guide here:  [http://ubuntuforums.org/showthread.php?t=801103](http://ubuntuforums.org/showthread.php?t=801103) and replaced my Mouse section in my xorg.conf with:

```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "evdev"
        Option      "evBits"        "+1-2"
        Option      "keyBits"       "~272-287"
        Option      "relBits"       "~0-2 ~6 ~8"
        Option      "Pass"          "3"
EndSection
```
I also changed the ServerLayout section to say InputDevice "Mouse0" instead of InputDevice "Configured Mouse".  After restarting X the mouse finally recognized the side buttons as buttons 8 and 9.  However, the scroll wheel didn't work, so after a bit more research I came up with the solution of adding the line:
```

xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"
```
to my System->Preferences->Sessions.  Truthfully I'm not sure why this is needed, but I couldn't get the scroll wheel to work any other way, and when I add that line, it works!  I tried putting the "pointer = ..." command in an Xmodmap file in a number of places as per the tutorials I read but I couldn't get it to automatically run whenever x started.  Maybe another day, I'm going to celebrate this victory.  Hope that helps.

---

