---
title: "Having res problems"
date: 2008-10-19
forum: General Help
---

### Post by Famdebruin on 2008-10-19
Installed ubuntu a few days ago and still have the same problem i only have 640x480 as resolution already tried a few solutions from the forum but none of them worked. Plz help me out its annoyingly BIG :p

---

### Post by PsychedelicReaction on 2008-10-19
have you installed the driver for your graphic card?

---

### Post by Famdebruin on 2008-10-19
yes that's the strange thing with the driver uninstalled it give a resolution of 1024x768 with it only 640x480. always used 1600x1200 so it's not the monitor

---

### Post by PsychedelicReaction on 2008-10-19
can you post the content of the file /etc/X11/xorg.conf?

---

### Post by Famdebruin on 2008-10-19
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

that's it

---

### Post by fooman on 2008-10-19
what video card are you using and how did you install the drivers?

---

### Post by Famdebruin on 2008-10-19
uhw rather long name here it is: MSI nx8600 GTS Diamond plus and when i enabled the compiz effects it said to enable the video driver i clicked on it and it downloaded the driver

---

### Post by Famdebruin on 2008-10-19
ehw anyone can help me out here?

---

### Post by fooman on 2008-10-19
you have an nvidia 8600.  you could try using envyng to install the drivers.  it is available in synaptic (system > administration > synaptic package manager).  when synaptic opens, search for "envyng-gtk" and install it. or you could install in a terminal...just run this command:

```
sudo apt-get install envyng-gtk
```

after it installs,  find it in applications > system tools > envyng.  open it and follow the prompts to install the nvidia driver.

hope that helps.

---

### Post by ant1060 on 2008-10-19
Hi!

I have often had resolution problems too since I started using Ubuntu.  There are two ways to solve them, as far as I know.  

One is manually to edit your xorg.conf (/etc/X11/xorg.conf)and insert a line with your monitor's resolution in the screen section (ask if you would like to try this...)

The other is to run in a terminal the following command : sudo dpkg-reconfigure -phigh xserver-xorg which allows NVIDIA to write the correct xorg.conf for your system, thus magically solving the resolution question.

As there's not much info in your xorg.conf, you might like to try doing that : BUT SAVE YOUR CURRENT CONFIG first so you can boot back into it if you make a mistake!

Good luck.

---

### Post by Famdebruin on 2008-10-19
> **fooman said:**
> you have an nvidia 8600.  you could try using envyng to install the drivers.  it is available in synaptic (system > administration > synaptic package manager).  when synaptic opens, search for "envyng-gtk" and install it. or you could install in a terminal...just run this command:

```
sudo apt-get install envyng-gtk
```

after it installs,  find it in applications > system tools > envyng.  open it and follow the prompts to install the nvidia driver.

hope that helps.

thx installing the nvidia driver now hope it works :)

---

### Post by Famdebruin on 2008-10-19
> **ant1060 said:**
> Hi!

I have often had resolution problems too since I started using Ubuntu.  There are two ways to solve them, as far as I know.  

One is manually to edit your xorg.conf (/etc/X11/xorg.conf)and insert a line with your monitor's resolution in the screen section (ask if you would like to try this...)

The other is to run in a terminal the following command : sudo dpkg-reconfigure -phigh xserver-xorg which allows NVIDIA to write the correct xorg.conf for your system, thus magically solving the resolution question.

As there's not much info in your xorg.conf, you might like to try doing that : BUT SAVE YOUR CURRENT CONFIG first so you can boot back into it if you make a mistake!

Good luck.

mmm installed the nvidia drivers but that didn't make a diference and when i try the command line you gave it says:
sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081019223556

and it doesn't change a thing for my resolution :s

---

### Post by Famdebruin on 2008-10-20
well its solved but still kinda strange it says i don't have a video driver and can't use compiz anymore but i can play games :s

Thx guys

---

