---
title: "[SOLVED] Sidewinder Gaming Mouse Configuration Help"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by r00tzz on 2007-11-15
Hi,

has anyone able to configure all buttons of a sidewinde gaming mouse?

The "down/back" button does nothing and the "up/forward" button acts like a right button.

TIA.

---

### Post by r00tzz on 2007-11-18
bump

---

### Post by r00tzz on 2007-11-19
Never mind :evil:! I already sold it. Let's start a new thread to see what bluetooth combo (keyboard+mouse)

By the way, I'm looking at these two choices:

Microsoft optical desktop elite for Bluetooth
[http://www.buy.com/prod/microsoft-optical-desktop-elite-for-bluetooth/q/loc/101/10375069.html](http://www.buy.com/prod/microsoft-optical-desktop-elite-for-bluetooth/q/loc/101/10375069.html)

and 
Logitech cordless desktop MX5000 Laser
[http://www.buy.com/prod/logitech-cordless-desktop-mx-5000-laser/q/loc/101/201935171.html](http://www.buy.com/prod/logitech-cordless-desktop-mx-5000-laser/q/loc/101/201935171.html)

let's see who's the winner!:lol:

---

### Post by r00tzz on 2007-11-23
REALLY SOLVED!!!!:guitar:

Here's the how-to:

first edit your xorg.conf
```
sudo nano -w /etc/C11/xorg.conf
```

and use the EVDEV driver
```

Section "InputDevice"
  Identifier      "Configured Mouse"
  Driver          "evdev"
  Option          "Name" "Microsoft SideWinder? Mouse"
  Option          "CorePointer"
  Option       "SendCoreEvents" "true"
EndSection

```

then create/edit the .xbindkeysrc file
```
sudo nano -w .xbindkeysrc
```

and put the following
```

# Mouse Buttons
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:9

```

now create/edit a 65mouse file under /etc/X11/Xsession.d/
```

sudo nano -w /etc/X11/Xsession.d/65mouse

```

and put the following line

```

xbindkeys

```

That's it, as simple as that!! 

Sorry for not mentioning the sources, but I tried a lot of stuff that were in the net. But the credit is not mine.

Hope I can help somebody!

---

### Post by cerebrix on 2008-02-29
my friend did it a bit differently today by commenting out my old config and adding the following config.

hope this helps someone, only change made was in the xorg.conf

```

Section "InputDevice"

        Identifier  "Configured Mouse"

        Driver      "mouse"

	Option	    "CorePointer"

        Option      "Protocol" "ExplorerPS/2"

        Option      "Device" "/dev/input/mice"

        Option      "Buttons" "5"

        Option      "ZAxisMapping" "4 5"

        Option      "ButtonMapping" "1 2 3 6 7"

        Option      "Emulate3Buttons" "no"

EndSection



#Section "InputDevice"

#	Identifier	"Configured Mouse"

#	Driver		"mouse"

#	Option		"CorePointer"

#	Option		"Device"	"/dev/input/mice"

#	Option		"Protocol"	"ImPS/2"

#	Option		"ZAxisMapping"	"4 5"

#	Option		"Emulate3Buttons"	"true"

#EndSection


```

---

