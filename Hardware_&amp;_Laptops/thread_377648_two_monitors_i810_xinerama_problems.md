---
title: "two monitors i810 xinerama problems"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by pisuke on 2007-03-06
I have been trying with no success using two monitors with Xinerama. The Laptop one, and an external CRT. I'm using de i810 driver for my intel integrated graphics card.

Amb running Edgy with last updates and I have followed all the howtos in the forums and also the reference on the wiki ([https://help.ubuntu.com/community/XineramaHowTo#head-293c9ec6c621bad38a16cfc937e194152d875966](https://help.ubuntu.com/community/XineramaHowTo#head-293c9ec6c621bad38a16cfc937e194152d875966))

In fact there is image on both monitors, but when i drag a window to the second one it gets stuck to a point and can't go no further. 

I can go everywhere with the mouse, but the right click or the selecting rectangle does not function in the second monitor.

Any clues? I tryied thousand possibilities without luck.

I attach my xorg.conf, but its the same you can find in the wiki.

Thanks.

```
Section "Device"
        Identifier      "Card-DualI"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
        Identifier      "Card-DualE"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
EndSection

Section "Screen"
        Identifier      "Screen-DualI"
        Device          "Card-DualI"
        Monitor         "Monitor-LCD"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen-DualE"
        Device          "Card-DualE"
        Monitor         "Monitor-CRT"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Monitor"
	Identifier	"Monitor-LCD"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor-CRT"
	Option		"DPMS"
EndSection

Section "ServerLayout"
        Identifier      "Xinerama"
        Screen          0 "Screen-DualI" 0 0
        Screen          1 "Screen-DualE" RightOf "Screen-DualI"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
        Option          "Xinerama" "true"
EndSection
```

---

### Post by pisuke on 2007-03-07
No one has this driver with xinerama working on edgy?

This worked for me one time but i lost de xorg.conf.:(

---

### Post by Oreo on 2007-04-02
I also wish someone would get i810 and xinerama working with Edgy or Fiesty.
I upgraded from Dapper to Edgy, and when I couldn't get xinerama to work,
I reverted to Dapper.
(And it wasn't easy to revert!)

Oreo

---

### Post by n2000 on 2007-07-09
i have the same problem:
[LIST]
[*]feisty
[*]i810
[*]screen 1: 1280x800
[*]screen 2: 1280x1024
[/LIST]
Xinerama ist working. I can move my mouse from one screen to the other. I can maximize windows on both screens. i can not drag an window from one screen to the other (just a little bit)...

---

