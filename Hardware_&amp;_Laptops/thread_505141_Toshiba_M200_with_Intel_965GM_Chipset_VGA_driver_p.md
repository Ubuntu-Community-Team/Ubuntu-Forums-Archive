---
title: "Toshiba M200 with Intel 965GM Chipset VGA driver problem"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by Jettechen on 2007-07-19
Dear all,
I have a toshiba Laptop with Intel965GM chipset. And it's WXGA LCD.
It's screen resolution should be 1280X800; but after I install the Ubuntu7.04, screen resolution was 1024X768

It seems the VGA driver not installed. I tried to install the xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb; then restart X, and restart the computer.
Both can't work.

I checked /etc/X11/xorg.conf; it seems I have 1280X800 secreen resolution?
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Default"
	Monitor		"Default Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

I am a pretty new to Linux. Is there any one can help me slove this problem?
Thank you very much.

---

### Post by w4ett on 2007-07-20
Fron the terminal type:

sudo dpkg-reconfigure -phigh xserver-xorg

and from the interface select your desired resolutions from the available options.

exit interface and press <Ctrl><Alt><Backspace> to restart X, and your new resolutions SHOULD be available.

---

### Post by Jettechen on 2007-07-20
@w4ett, thank you.
I tried your method, but after I restart X. my X won't start any more...
I'm still waiting for the sloution

---

### Post by w4ett on 2007-07-20
If X didn't restart, you didn't select the correct intel driver before you selected the resolutions.

you can do it again from the recovery mode CLI:


sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Jettechen on 2007-07-20
@w4ett, it seems not slove the problem.
everytime I set the VGA to Intel, and resolution 1280X800, then restart X. The LCD became black out.
The X nerver shows.

Kept waiting for the solution.

---

