---
title: "nVidia driver troubles... (A few system queries, too)"
date: 2008-07-19
forum: General Help
---

### Post by Galveru on 2008-07-19
System Specifications (To the Best of my knowledge):
10+ year old computer.
Pentium II (800-900 MHz) Processor
128 MB of RAM
nVidia SGS Thomson (Joint Venture) RIVA128 Graphics Card (rev 10)
GNOME
Ubuntu 8.04 Hardy Heron
Driver in use: nv (I would like to know how to disable this. nv does not show up in the "hardware drivers" interface)

I think that sets the scene here. So I am trying to install a more tuned nVidia driver (The latest Legacy) onto this aging computer, and it gives me an error (wahh nothing works on the first time :P) :

ERROR: Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s).
[[Extra]]
Please see the log entries 'Kernel module load error' and 'Kernel messages' at the end of the file '/var/log/nvidia-installer.log' for more information.
[[Next page]]
ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.og' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [http://www.nvidia.com/](http://www.nvidia.com/)

I have gone into Hardware Drivers, and there are NO drivers whatsoever listed.  So...how do I uninstall/disable the built-in driver nv so I can install?  Am I doing this completely wrong?
Is there a command that can check to see if a program is already installed?  (Something like sudo apt-get check [program])
Any help would be greatly appreciated.

---

### Post by erginemr on 2008-07-19
I guess you need to install a few more packages for the NVidia installer, such as "build-essential" and "xorg-dev". You can install these from Synaptic.

Another point is to make sure that X is not running during the installation from the "NVidia-*.run" installer.

Or you may give a shot with EnvyNG, which automates the installation of NVidia/ATI drivers.

---

### Post by jonian_g on 2008-07-19
Installing the driver from the nvidia website is a really bad idea.
The best way to do it is with the Restricted Drivers Manager or EnvyNG (has newer versions of the driver).

Why it's a bad idea? Because every time you get a kernel update (three times till now after Hardy released), you have to reinstall the driver.

So you might try this:

Open synaptic and completely remove everything that starts with nvidia-glx-*

Uninstall the driver that you downloaded from the nvidia website. You must have the file and follow the same procedure when you installed it and type:

```
sudo sh NVIDIA*.run --uninstall
```

Delete xorg.conf in /etc/X11 and reboot.

Then open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System Tools>EnvyNG and install the driver.

---

### Post by Galveru on 2008-07-19
> **jonian_g said:**
> Installing the driver from the nvidia website is a really bad idea.
The best way to do it is with the Restricted Drivers Manager or EnvyNG (has newer versions of the driver).

Why it's a bad idea? Because every time you get a kernel update (three times till now after Hardy released), you have to reinstall the driver.

So you might try this:

Open synaptic and completely remove everything that starts with nvidia-glx-*

Uninstall the driver that you downloaded from the nvidia website. You must have the file and follow the same procedure when you installed it and type:

```
sudo sh NVIDIA*.run --uninstall
```

Delete xorg.conf in /etc/X11 and reboot.

Then open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System Tools>EnvyNG and install the driver.

I maybe a complete idiot for following you, or screwing up something, but now every time I boot Ubuntu, it starts in Low-graphics mode and a configuration prompt comes up.  What have I done wrong?

---

### Post by jonian_g on 2008-07-20
Did you do everythig as I said?
Are you sure you deleted xorg.conf?

Don't worry, nothing is screwed, everything can be fixed.

---

### Post by jonian_g on 2008-07-20
Open Synaptic an check if nvidia-glx-legacy-envy or nvidia-glx-envy is installed. If not this means the driver is not installed. Try installing it again with envy and manualy choose the driver that starts with 73.*.

If it fails then open a terminal and type:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

and will get back to where you were before doing what I told you.

---

### Post by Galveru on 2008-07-20
Do you mean 71.*.*?  There is no nVidia with 73.  (Might be common sense, just wondering)

---

### Post by jonian_g on 2008-07-20
The 7*.* are the legacy drivers so it doesn't matter if it is 71 or 73. Mine shows 73.*, envy was updated 2 days ago (I have the backports repo enabled. Maybe it's from the backports)

---

### Post by Galveru on 2008-07-20
Okay, the packages were installed and everything...but it still boots in low-graphics mode.  Can I put back Xorg.conf and still have the driver working?

---

### Post by jonian_g on 2008-07-20
I don't think so... Put back xorg and retry to install the driver.

Do you have only low res mode or you get the config screen on boot?

If you have only the low res then type:

```
sudo displayconfig-gtk
```

and choose your monitor model or a generic model with your resolution. Close this window and you will be able to change resolution.

---

### Post by Galveru on 2008-07-26
I replaced Xorg.conf and then installed the driver.  I configured the file and used cp to replace the old Xorg.conf with the new one created from the gtk-config.  I know how frustrating this might be for you, but keep in mind this is a ten year old computer.
The text shown at startup (along with the "Shut Down" "Continue" and "Configure" options) is relative to, "We could not detect your hardware [or drivers, respectively?], please configure it now."
I put my monitor type and everything, but it will not work.

Again, sorry for being so troublesome.

---

### Post by Nopposan on 2008-09-09
I'm having basically the same issue with an old Dell computer.

---

### Post by Nopposan on 2008-09-09
O.K.  I solved my problem.  Hopefully this will help for you too.

Reinstall the driver using Envy like you did the first time.

Then reboot like it asks you to.  Note all of the info you can find about your monitor, by the way.

Now when you reboot you may be forced to reconfigure the xserver.  That's good, cause that's what happened to me.  Go ahead and do this reconfiguring and after you've successfully TESTED the nvidia legacy driver AND the monitor, remember to SAVE the settings to the file /etc/X11/xorg.conf.  You have to type that path directly into the address bar at the top of the gui dialog box and press the little "save" (floppy disk icon) or your settings will be lost.

Now, when you see the gdm login screen it should be at 1024x768 resolution, but when your gnome session begins it will be at the last setting you actually used in gnome.  Don't worry, all you have to do is go to System --> Preferences --> Screen Resolution and select 1024x768.

Just for good measure, here's my xorg.conf file.  Note that there's nothing saying "Virtual" after the Depth 24 setting.:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA Legacy"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"NEC"
	Modelname	"NEC MultiSync LCD1550V"
	Horizsync	31.0-60.0
	Vertrefresh	55.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Hope this works for you.

Cheers.

---

