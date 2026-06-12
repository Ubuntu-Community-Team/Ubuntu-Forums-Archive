---
title: "How do I enable mouse buttons 4 &amp; 5?"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by MindRiot on 2007-01-14
Hello.

I have the following mouse:

[IMG]http://img152.imageshack.us/img152/4403/pd745prg1.jpg[/IMG]

I use my mouse with my left hand as often as my right hand so this mouse is perfect since its symmetrical. 

I was hoping someone could tell me how I could utilize mouse button four and mouse button five in Ubuntu.

Is there a way to enable these mouse buttons and assign them to perform specific functions? 

Would be nice if I could Back and Forward in both my web browser and applications like Image Viewer with mouse button four and mouse button five.

---

### Post by monolegis on 2007-01-17
I would also like to utilize these buttons on my mouse? Anyone got an idea on how to fix it?

---

### Post by GeBo on 2007-01-21
Open a terminal

Type: sudo gedit /etc/X11/xorg.conf

Find the part that says:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                 "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"       "4 5"
        Option          "Emulate3Buttons"   "true"
EndSection

Add two lines to this section:
	Option		"Buttons"		 "7"
	Option		"ButtonMapping"      "1 2 3 6 7"

Restart Gnome by CTRL-ALT-BACKSPACE (don't be afraid if it takes more a second to reload).

That should do it.

---

### Post by tweedledee on 2007-01-21
If the above suggestion doesn't work (if so, probably b/c the buttons aren't recognized as 6 & 7), try here: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).

---

