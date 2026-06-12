---
title: "how to disable sypanptics touchpad ?"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by syxbit on 2006-06-20
in win XP there's an option in the driver to disable the touchpad when you plus in a usb mouse.
this is really handy, as i rarely use the touchpad (almost always have a usb mouse)
if there's no option to quickly disable it or disable when i plug in a mouse, how can i permanently disable it ?
thanks

---

### Post by nanotube on 2006-06-20
not sure if there is a handy way to disable it automagically whenever you plug in your usb mouse... maybe someone else can come up with something.

but to disable it permanently, first, make a backup of your X config file with command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then edit your /etc/X11/xorg.conf file, using command
```
sudo nano /etc/X11/xorg.conf
```
and remove the section that looks somewhat like this:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```
then restart X (or the whole computer), and your touchpad should be inoperative.

---

### Post by syxbit on 2006-06-20
permanent is fine. i could enable it without too much fuss, 

i deleted the following lines

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

but then Xserver doesn't start up upon reboot
i had to restore my backed up xorg.conf for it to work

am i doing something wrong ?

---

### Post by pataphysician on 2006-06-20
i'm not sure about this, but i think that at the end of your xorg.conf file, you can just comment out the input device line:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
       InputDevice     "stylus" "SendCoreEvents"
       InputDevice     "cursor" "SendCoreEvents"
       InputDevice     "eraser" "SendCoreEvents"
#        InputDevice     "Synaptics Touchpad"
EndSection

```

again i'm not sure, but, you know, if it doesn't work you can re-edit it or restore your back-up again.

---

### Post by spier on 2006-06-20
I was  after this funtionality, too, and found this howto, that do the job:

[HOWTO: Turn Touchpad On and Off On your Laptop]("http://www.ubuntuforums.org/showthread.php?p=814772#post814772")

---

