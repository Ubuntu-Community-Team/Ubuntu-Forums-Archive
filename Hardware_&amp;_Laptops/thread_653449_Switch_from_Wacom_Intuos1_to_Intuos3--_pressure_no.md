---
title: "Switch from Wacom Intuos1 to Intuos3-- pressure not working"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by taquito on 2007-12-29
So, my old Wacom Intuos1 (Model GD-0405-U) bit the dust, and I replaced it with a shiny new Intuos 3 (Model PTZ-431W).  Unfortunately, now pressure doesn't work properly.

Here's the run down:

Before setting up the new tablet:

--I had a Wacom Intuos (Model GD-0405-U), working properly with Gimp and Inkscape (pressure and everything!)
--I had wacom-tools and xserver-xorg-input-wacom packages installed (and still are, though I tried uninstalling and reinstalling)
--my /etc/X11/xorg.conf file had the following lines: (and still does)

> Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


**and**

> Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection




I now have a Wacom Intuos 3 (Model PTZ-431W)


--I plugged it in and restarted X.  Both the pen and mouse function as a pointer, but there is no pressure data coming in.  Also, the buttons and touchpad do nothing, but that is another issue
--doing "wacdump /dev/input/wacom", position and button clicks are working as would be expected, but there is no pressure.  Model, vendor, etc. come up as "unknown" 
--using gimp or inkscape, going to File->Input Devices... I get "No extended input devices"
--I have also added the following to my /etc/X11/xorg.conf file:

> Section "InputDevice"
	Driver "wacom"
	Identifier	"pad"
	Option	"Device"	"/dev/input/wacom"
	Option	"Type"	"pad"
	Option	"USB"	"on"
EndSection

and Section "SeverLayout" was updated accordingly:

> Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"pad"	#for intuos3 tablet
EndSection


--doing "xsetwacom list dev" outputs:

stylus           pad
cursor           cursor
eraser           eraser
pad              unknown

--doing "xidump -l" outputs:

Configured Mouse               disabled
Generic Keyboard               keyboard
NVIDIA Event Handler           extension
stylus                         extension
cursor                         extension
eraser                         extension
pad                            extension

--I also downloaded the linux wacom driver (0.7.8-3), but was unable to get it to compile during the first few attempts-- I'm not 100% sure that it's needed though?  (Should already be built in, and I am given to understand that the Intuos3 4x6 has been supported since the 0.7.6-4 version of the wacom driver?)

-- "sudo lshw|grep WACOM" outputs nothing

--"lsmod|grep wacom" outputs:

wacom                  15232  0
usbcore               130820  5 wacom,usbhid,ehci_hcd,ohci_hcd

- I also tried installing package "wacom-kernel-source" just for fun, but, to no avail.

--I am currently running ubuntu 6.06, kernel is 2.6.15-29-386


Any help is greatly appreciated.  Thanks!

---

