---
title: "Monitor not showing in System Settings"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by reb68 on 2007-03-15
After installing 6.10 I find the monitor is not in "system Settings" I need to change the resolution from 800 to the larger resolution. (or about there)
Is there another place to make the change?

---

### Post by taurus on 2007-03-15
You can change the resolution in /etc/X11/xorg.conf.  Open a terminal and edit it, near the end.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

And of course, you also need to install a driver for your graphic card before you can go to a higher resolution.  What kind of graphic card do you have on your machine anyway?

---

### Post by reb68 on 2007-03-15
I do not know what graphic card I have but I had the higher resolution before the upgrade. This is what I get in the terminal:
"(gksudo:5111): Gtk-WARNING **: cannot open display:
root@dick-desktop:~#"

---

### Post by taurus on 2007-03-15
To see which graphic card you have on your machine, run this command from a terminal.

```
lspci
```
And if "gksudo gedit" doesn't work, then you can always use a text editor like nano.

```
sudo nano -Bw /etc/X11/xorg.conf
```
To save and exit, press <Ctrl>o and then <Ctrl>x.

p.s.  For Kubuntu user, the command is

```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by reb68 on 2007-03-15
I loaded the file in Kate and this is what I have. Where do I make the change?
------------------
Section "Monitor"
	Identifier	"DELL D1025TM"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
	Monitor		"DELL D1025TM"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by taurus on 2007-03-15
So you have an ATI graphic card.  I guess you need to install a driver for it before you can get a higher resolution.  Maybe this link helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by reb68 on 2007-03-15
I installed the repository and then the driver. What is my next step.

---

### Post by taurus on 2007-03-15
If you just finished installing a driver for your ATI card, reboot and see if it works.  If it is, then you can use a higher resolution now.

---

### Post by reb68 on 2007-03-16
The monitor icon is now is system settings/computor administration. It still only gives me the two choices, 640X480 and 800X600. Is there a place to edit this. 
Now I keep getting a popup window:
-----------------------
sorry
Could not find Mime Type
Application/octet-stream
---------------------------------
Is this related to the problem?

---

