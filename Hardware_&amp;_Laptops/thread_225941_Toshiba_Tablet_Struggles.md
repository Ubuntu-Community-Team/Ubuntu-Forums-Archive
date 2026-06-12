---
title: "Toshiba Tablet Struggles"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by jharbert on 2006-07-30
I have a Toshiba Portege M205 and I haven't been able to get the tablet pen to work.  I've tried several different approaches that I've found online such as setserial and changing /dev/wacom to /dev/input/wacom in the xorg.conf file.  Still no luck.  Any ideas (or step by step instructions incase I was doing something wrong).  Thanks a lot.

[COLOR="Red"]Edit:[/COLOR]
For I found a quick and easy way to get it to work for anyone who is still trying to get their tablet running.  Follow these instructions:
[http://www.ubuntuforums.org/showthread.php?t=184542]("http://www.ubuntuforums.org/showthread.php?t=184542")

---

### Post by 23meg on 2006-07-30
Please post the contents of your xorg.conf file. Do you get any action in wacdump when you move the stylus?

---

### Post by jharbert on 2006-07-30
Here's my xorg.conf file.

```

[...]

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

[...]

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

When I try running wacdump for on ttyS0 I get the following error:
WacomOpenTablet: Invalid argument

In my most recent attempt I was following the instructions here:
[http://www.ubuntuforums.org/showthread.php?t=152118]("http://www.ubuntuforums.org/showthread.php?t=152118")

Thanks for your help

---

