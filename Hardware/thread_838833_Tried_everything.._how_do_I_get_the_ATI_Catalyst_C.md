---
title: "Tried everything.. how do I get the ATI Catalyst Control Center"
date: 2008-06-23
forum: Hardware
---

### Post by rickcr on 2008-06-23
I'm stumped. I have a Compaq 6910p laptop that has Mobility Radeon X2300 video driver. I've install fglxr and the fglxr-control-center with synaptics (and even tried the envy versions). I can't seem to find an ati control center anywhere. I've googled and tried to find fglxr control center related things in my bin dir, but no luck. What am I doing wrong?
(I tried to also get the linux drivers from ati's site but for some reason they don't have the X2300 version.)

My graphics are fine looking, but I'd like a better gui for getting my dual monitor setup working. I read the big desktop post and got it sort of working, but it needs a lot of tweaking so figured I'd try the control center since I had luck with it when I was on SuSE 10.3. 

Thanks

---

### Post by jocko on 2008-06-23
Have you tried typing "amdcccle" in a terminal?
The catalyst conrol center is part of the xorg-driver-fglrx package, but it does not make any menu item.

---

### Post by rickcr on 2008-06-24
Thanks Jocko! That was it. 

Newb question, but how would someone know to use that command? That's one thing I find frustrating with Linux is if an install takes place how do I know the command to start it if I don't see a gui app starter in any of my menus?

---

### Post by Canis familiaris on 2008-06-24
> **rickcr said:**
> Thanks Jocko! That was it. 

Newb question, but how would someone know to use that command? That's one thing I find frustrating with Linux is if an install takes place how do I know the command to start it if I don't see a gui app starter in any of my menus?

If you install Ati drivers through Ubuntu repos it generally does not create shortcut in the menus. 
However if you install it via envy then it does create the shortcut.
However you can create a shortcut now.
Right Click on the Applications Menu. Choose Edit Menus.
Choose any submenu and click on Add item and name it whatever you can and the command is, as you now know, amdcccle

---

### Post by rickcr on 2008-06-24
Thanks Anurag, I'll do that.

Now I have another issue to work out. In the ATI control center I can't seem to set the resolution (or refresh rate) of the laptop and external monitor. The resolutions need to be different. I'm not afraid to modify xorg.conf but when I opened it up it was very confusing since it didn't seem to typical things in my xorg.conf including not even showing two monitor sections? Should I manually start hacking up this file? I notice there is a /etc/ati/amdpcsdb file which seems to have some xorg.conf-like info, but not sure if I should be messing with that? 

Googling seems to bring up so many conflicting things to do, so I'm not sure what to attempt. Thanks for any advice.

My xorg.conf looks like:


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
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
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "0x0+0x0"
	Option	    "EnableMonitor" "crt1,lvds"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

---

### Post by Canis familiaris on 2008-06-24
Maybe this link will help

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

EDIT: I think the previous link is wrong, try this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by rickcr on 2008-06-24
In case anyone else searches the forum and gets this post adding the following to my xorg conf device section did the trick:

Option "DesktopSetup"  "horizontal" #Enable Big Desktop
Option "Mode2"         "1280x1024" #Resolution for second monitor
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.

I got the info from section 2 from this link: [http://ubuntuforums.org/showthread.php?t=301941]("http://ubuntuforums.org/showthread.php?t=301941")

---

