---
title: "Serious headache with Xconfig"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by Hg80 on 2005-08-16
IM trying over and over agin to get X to run at 1280*1024 as i use to with mandrake 9 and still do with windows but when ever i config X to do so i get many different errors
including:
Screen found but no possible modes found (something like that)
And something about my graphics not being able to support the 16/24 bit modes

I have a Samsung SyncMaster753DFX Monitor (30 – 70 kHz Hor. Frequency and 50 – 160 Hz Vert. Frequency))
A ATI 9800PRO 128MB graphics card

please help as i dont like using linux or any desktop in 1024*768

---

### Post by tonysathre on 2005-08-16
was the error a "screens found but none with a working configuration" ?

---

### Post by varunus on 2005-08-16
Have you installed the proprietary ATI drivers?  Can you post your /etc/X11/xorg.conf file?

---

### Post by Hg80 on 2005-08-17
[QUOTE=tonysathre]was the error a "screens found but none with a working configuration" ?[/QUOTE]

Yeah it was

and as regards posting the xconfig file i cant get into x to do so

---

### Post by tseliot on 2005-08-17
Ok, type:

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the lines with the resolution and add (or substitute) the resolution you need. For example:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"[COLOR=Red]1024x768[/COLOR]"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"[COLOR=Red]1024x768"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"[COLOR=Red]1024x768[/COLOR]"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"[COLOR=Red]1024x768[/COLOR]"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"[COLOR=Red]1024x768[/COLOR]"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"[COLOR=Red]1024x768[/COLOR]"
	EndSubSection
EndSection

For example put "1280x1024" instead of the word in red.

after you've modifed the file (you can only use the keyboard in this case)

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit 

/etc/init.d/gdm start (or "kdm start" if you use KDE)

Tell me if it works

---

