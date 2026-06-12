---
title: "Tablet PC stylus always on right click (eraser)"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Evo Pete MTL on 2007-05-21
Hi everyone,

My tablet PC features worked well with Edgy Eft. When I upgraded to Feisty Fawn for a reason I ignore my stylus is always on right click (eraser). When I press the eraser is stays on right click. Btw I'm a noobie hehe

Here is my script for the stylus stuff:

#!/bin/bash

orientation=$(xrandr -q | grep rotation)
	
if [ "$orientation" = "Current rotation - normal" ];
then
	xrandr -o right
	xsetwacom set "stylus" Rotate CW
	xsetwacom set "cursor" Rotate CW
	xsetwacom set "eraser" Rotate CW
	orientation="right"
else
	xrandr -o normal
	xsetwacom set "stylus" Rotate NONE
        xsetwacom set "cursor" Rotate NONE
        xsetwacom set "eraser" Rotate NONE
        orientation="normal"
fi


Here is the part of my xorg.conf for tablet stuff:

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

---

### Post by Evo Pete MTL on 2007-05-31
Nobody is able to help me with this? Please!!! hehe

---

### Post by mrming on 2007-06-10
I had this problem too. Managed to fix it with the following command:

xsetwacom set stylus button1 1

---

### Post by Evo Pete MTL on 2007-06-10
Sick I'll try that when I have time. Thanks so much!

---

### Post by stephanecharette on 2007-07-24
The "right-mouse-click" stylus button wasn't working for me on any of 6.04, 6.10, and 7.04.  I recently found out about xsetwacom, and through trial and error discovered the right combination that now has things up and running.  In case anyone else is stuck with this problem, see if this helps:

xsetwacom set stylus Button1 "button 1"
xsetwacom set stylus Button2 "button 1"
xsetwacom set stylus Button3 "button 3"

In my case, this is using a Wacom Intuos 9x12 USB with the stock stylus that shipped with the tablet.  I'm currently running Ubuntu 7.04, and a search of "Wacom" in Synaptic shows I have the following packages installed:

- wacom-tools, v1:0.7.7.7-0ubuntu1
- xserver-xorg-input-wacom, v1:0.7.7.7-0ubuntu1

(The Wacom mouse works fine except for the side scroll wheel...haven't figured out how to get that part to work yet, though this is now a non-issue since the stylus seems to be working.)

---

### Post by oofnik on 2007-08-23
> **stephanecharette said:**
> 
xsetwacom set stylus Button1 "button 1"
xsetwacom set stylus Button2 "button 1"
xsetwacom set stylus Button3 "button 3"

Thanks!! Just what I needed to get the pen button working for right click on my Lenovo X60 tablet. I put a little script that executes this at startup. :)

---

