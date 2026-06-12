---
title: "[SOLVED] Help! I just want one big display, ATI card."
date: 2008-09-23
forum: Hardware
---

### Post by Mattlock on 2008-09-23
The problem is I'm using a laptop and can't seem to find a way to just run one monitor (19" widescreen at 1680*1050). My laptop one is able to be set fairly easily, it's just that the main one is being a pain.
I just converted to full-Ubuntu and having serious issues trying to fix such a simple problem! I had to get the ATI drivers, and finally got things working using:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way")

Is there a way to edit my xorg file easily maybe? I fix the resolution in the OS at all (even in displayconfig-gtk)

Heres the xorg:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Thanks in for any help in advance... This is causing me a headache.
PS: graphics card is an oldschool x1400 (a pain to get drivers for as they're pretty much 1300 with extra 128mb chucked on).

---

### Post by Mattlock on 2008-09-23
No one?

---

### Post by travm on 2008-09-23
I dont fully understand your problem, but it sounds similar to one I was having on my desktop hooked up to my TV.  It would default my screen0 to my tv, which i did not want, and caused funny behaviour during boot and operation.  basically it just wouldnt work right.  
I solved it by installing the catalyst 8.9 driver following the same guide.  
I ran into a minor problem but I updated teh wiki to 8.9 so al should be good now.

---

### Post by SilverAdder on 2008-09-23
Are you trying to have dual display with one big desktop? Or two desktops? Or move the desktop to the big screen, disabling your laptop? I don't quite follow...

---

### Post by Mattlock on 2008-09-23
Sorry, I want to move the desktop my main LCD disabling my laptop!

---

### Post by markbuntu on 2008-09-23
You can do that in the Catalyst Control Center which you can find in Applications/Other. No need to edit your xorg.conf. Once you get there , it should be fairly easy to figure it out.

---

### Post by Mattlock on 2008-09-23
Oh you got to be kidding me! didn't see it, was under accessories. Thanks a bunch  I can stop yelling at monitor now.

---

