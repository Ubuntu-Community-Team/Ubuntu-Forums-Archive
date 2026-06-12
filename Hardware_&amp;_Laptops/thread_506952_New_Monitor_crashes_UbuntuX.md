---
title: "New Monitor crashes Ubuntu/X"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by bilbothebaggins on 2007-07-22
Hello.

My parents have bought a new (cheap) flatscreen monitor (1280x1024) for their Ubuntu box. Before we had an CRT hooked up to the box.
When we hook up the monitor to the PC and boot up the system crashes when the login screen should be shown. The boot logo of Ubuntu is shown just fine, but when the screen should switch to the login screen, the screen goes just black and no input in accepted anymore (CTRL+ALT+BACKSPACE does not work; pressing num-lock will not switch on the keybrd led)
When I do not attach the monitor at bootup, but wait a bit and plug it in only after the login-screen is shown, its working.

Any ideas why the monitor would crash Ubuntu/X :confused:

thanks!

Snip from xorg.conf:
```
Section "Monitor"
	Identifier	"T920"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"T920"
	DefaultDepth	24
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

---

### Post by w4ett on 2007-07-22
You must reconfigure your xorg.conf.........You can do it manually  from the CLI using:

```
sudo nano /etc/X11/xorg.conf
```

OR (also from CL)I:

```
sudo dpkg-reconfigure xserver-xorg
```

---

