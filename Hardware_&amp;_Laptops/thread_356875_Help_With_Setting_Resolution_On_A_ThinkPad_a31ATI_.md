---
title: "Help With Setting Resolution On A ThinkPad a31/ATI Radeon Mobility 7500"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by n1nj4Lo on 2007-02-08
I have been trying to find something to download that allow me to set my screen res to something higher than 800 x 600, As stated in the thread title I am on a IBM ThinkPad a31 which uses an ATI Radeon Mobility 7500.... I'd love to be able to use a different resolution for my screen, I can deal with not having dual display... Thanks in Advance for all Help and Advice..

~Xhris

---

### Post by woland on 2007-02-09
I assume you are a newbie to Linux. I apologize if it isn't so.

If System -> Preferences -> Screen Resolution doesn't allow you any other resolutions besides 600x800, then you should take a look at your /etc/X11/xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```
This will open the config file in text editor.
Find a section that looks like this:
```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
You can add the missing resolutions, save, exit the editor and reboot or restart the Gnome (Ctr+Alt+Esc).
Can you find out, what kind of display adapter your laptop has? Make sure that it matches the first line of this section. If not, search the forum for a guide to install the correct drivers.

---

### Post by n1nj4Lo on 2007-02-10
> **woland said:**
> I assume you are a newbie to Linux. I apologize if it isn't so.

If System -> Preferences -> Screen Resolution doesn't allow you any other resolutions besides 600x800, then you should take a look at your /etc/X11/xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```
This will open the config file in text editor.
Find a section that looks like this:
```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
You can add the missing resolutions, save, exit the editor and reboot or restart the Gnome (Ctr+Alt+Esc).
Can you find out, what kind of display adapter your laptop has? Make sure that it matches the first line of this section. If not, search the forum for a guide to install the correct drivers.

Yes I'm a newbie to Linux, But am loving it at the moment... I tried unhooking my secondary monitor and rebooted and it let me adjust the res jus fine... I guess I can live without the dual display for now...

---

### Post by woland on 2007-02-10
When I experimented with dual display, I had to modify the xorg.conf file, to enable all the resolutions.

Welcome to Linux! I was in your shoes 20 month ago. Good luck!

---

