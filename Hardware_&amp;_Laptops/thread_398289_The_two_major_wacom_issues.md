---
title: "The two major wacom issues"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by mukiex on 2007-03-31
I'm having the two most common problems with my Graphire4 pad : 
1. The mouse that comes with it has to be lifted over half an inch to stop registering movement, which is frustrating if you need to lift it often (and given the graphire pad's size, is quite often, and makes the mouse nearly useless).
1.a. I've set CursorProx in xorg.conf to a much smaller figure than is standard for my model (42), but there's no effect whatsoever.
2. My scroll wheel is reversed on that same mouse. Under "cursor", whether I set Zaxismapping to "4 5" or "5 4" makes no difference whatsoever.

Any help would be greatly appreciated, as this thing almost works PERFECTLY. (plus in general the mouse's movement is a TON more realistic and intuitive than in Windows, where I couldn't find a good accelleration/speed combination to save my life; before trying it in kUbuntu, I just thought the mouse didn't work right due to an inate flaw in the product)

Anyhoo, I'm in Kubuntu Edgy, no new packages, kernel 2.6.17-10-generic.


The relevant xorg.conf info :

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
#  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option "CursorProx" "4"
  Option 	"ZAxisMapping" " 5 4"
EndSection


	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"pad"

---

### Post by mukiex on 2007-04-01
EDIT : THIS [BLEEP] IS BROKEN. I guess I'll wait for Feisty.

---

### Post by calraith on 2007-04-05
Number 1 is a hardware thing.  Not much can be done about that with any software tweaking.
Number 2, I have the same issue with the mouse wheel scrolling the wrong direction.  However, I have been able to work around that by switching buttons 4 and 5 using xmodmap.
```
xmodmap -e 'pointer = 1 2 3 5 4 6'
```
If it works, put that command into a file, chmod the file 755, and auto launch it on session login.

---

### Post by mukiex on 2007-04-22
I fixed #1. The latest linuxwacom install (included in feisty?) does the trick. Cursorprox works, and lifting the mouse is just as easy as it is in Win 'n Mac.

However, the button thing is, for lack of a better term, f***ing broken. Switching in xmodmap doesn't fix it. Switching in KDE doesn't fix it. Failying those two, I tried xsetwacom. This is where the f***ing broken nature lies.

1. xsetwacom, when you set a button, for reasons I'll never understand, sets the button before it to the same value. So if you set button2 to "button 3", both the middle mouse and left mouse buttons become right-click.

2. with that in mind, even if you figure that out, button4 and button5's assignments mean nothing and do not affect scrolling. NOTHING seems to affect f***ing scrolling. The driver seems DEAD SET on making your mouse scroll in the wrong f***ing direction no matter what you do.

Note : There wouldn't be so much anger if I didn't try like TEN F***ING WAYS to get around a broken scroll assignment, only to have this STUPID F***ING DRIVER manage to not work EVERY SINGLE TIME.

BTW, I tried the expresskeys hack. the driver STILL tries to fight it (scrolling now jitters as the driver tries to send down-scroll while expresskeys sends up-scroll and vice versa) and if I press the left mouse button it segfaults.

Between Wacom and Ati I'm not sure who's failed me harder. >_<

---

### Post by mukiex on 2007-05-29
FIxed in latest linuxwacom beta. Specifically, installing the latest compiled wacom.ko

---

### Post by anindya_m on 2008-02-13
I got a wacom bamboo fun with mouse recently, and was quite annoyed with the mouse wheel issue (the driver is otherwise GREAT, btw). The xmodmap/xwacomset fixes did not work for me. I used the beta driver compiled from source, version 0.7.9-7.

It turns out, however, the problem is not serious. After about 30 mins of browsing the source I was able to fix this in the driver itself, and now the scroll wheel is working properly :) without any external tweaks.

If anyone is interested I will be happy to provide the patched driver, till the developers fix it.

---

