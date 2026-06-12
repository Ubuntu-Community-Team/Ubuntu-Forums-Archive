---
title: "How to install Dual Monitors"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by sugarbear.rick on 2007-05-31
Hello
 Bare  with me I am new to this glorious software

I have  two monitors on the same card, I would like to  run both monitors like I do when forced to use Microcrap Windows
 thanks any help would be appreciated

---

### Post by tropicflite on 2007-05-31
Try this:  

From the command line type

sudo gedit /etc/X11/xorg.conf

and enter your password

type control-f and search for

Section "Screen"

add the following two lines right below Defaultdepth


Option		"TwinView"	"True"
Option		"TwinViewOrientation"	"RightOf"

type control-s (to save the file)

type control-q (to close gedit)

type control-alt-backspace (to restart X)

That should do it.

---

### Post by jon_h on 2007-05-31
You want to put the Option "TwinView" "True" in the section for the nvidia device, not the screen. I've been having problems with the screen res with nvidia twinview, so no garuntees that it'll work perfectly.

---

