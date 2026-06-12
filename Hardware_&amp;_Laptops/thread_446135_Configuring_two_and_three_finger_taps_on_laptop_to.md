---
title: "Configuring two and three finger taps on laptop touchpad"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by peedeeramone on 2007-05-16
When I ran windows on this machine i used to be able to do two and three button clicks. i had them configured to go foreward and backward on the browser.

in Ubuntu, two finger taps seem to middle click and three right clicks. I am sure there is some sort of configuration file somewheres that I can use to configure this, but i am not sure where it is or exactly how to configure it to go foreward and backwards

if anyone knows how to do this please let me know


thanks

---

### Post by benanzo on 2007-05-16
You want to investigate your /etc/X11/xorg.conf file.  Under the section for Input Device (there may be multiple, just find the one that has "synaptic" as the driver) You can configure the actions for TapButton1, TapButton2 etc.  I am not exactly sure what the setting would be for what you want, but that is where I would start looking.  restart the X Server:
CTRL-ALT-F2
then:
```
sudo /etc/init.d/gdm restart
```
for the changes to take effect.

---

### Post by peedeeramone on 2007-05-16
i didnt see anything about that....

ill list all of the input devices i have:



Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


idn why theres a stylus and stuff for a touchpad but whatever...
i have a laptop but not a tablet....

also, i guess while im at it where do i go to configure the "media key" or whatever it is for the aplication launcher button?
i have a browser, mail, and another assignable application launcher key. the browser and mail keys work but the other one does nothing. i think i remember seeing somewheres how to configure it but i forget...

---

