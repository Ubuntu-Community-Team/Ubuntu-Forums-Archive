---
title: "ATI control center does weird things"
date: 2009-03-25
forum: Hardware
---

### Post by sanderd17 on 2009-03-25
Hi, a about two days ago I've installed new ATI drivers (via "Hardware drivers" in the system menu) for my graphical card because with the drivers I had  I couldn't open google earth or celestia.
Since I've installed those drivers, each time I log in my wallpaper is stretched to about 4 times the normal size and the little desktops in the lower right corner are about twice the size they should be. But if I open "ATI catalyst control center", the only way I found to set up my graphical card, and select an other resolution and afterwards cancel that resolution everything is back to normal.
How could I solve this, it looks pretty ridicule to see only a quarter of your wallpaper.

---

### Post by pkkid on 2009-05-26
Just chiming in to say I am having the same exact issue, so its notj ust you.

---

### Post by artsci2 on 2009-05-26
I also have trouble and cant find the file that keeps the monitor specifications for the driver to use. The xorg.config:

>>>>>>>>
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
<<<<<<<<<<

does not show any detection of my monitor and using "detect displays" under the system>preferences>screen resolution window does nothing to detect my two Sceptre 1680x1050 displays. I am only offered the choice of 3200x1200 in Big Desktop mode from the catalyst control center.

I would like to make the system boot to a 3360x1050 Big Desktop at 60fps

I had this once but lost it after trying to "upgrade" from 8.10 then reinstalling 8.10 doesnt seem to get it back.

---

