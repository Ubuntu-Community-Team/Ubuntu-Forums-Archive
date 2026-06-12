---
title: "ATI Dual Screen - Compiz doesn't start"
date: 2008-09-25
forum: General Help
---

### Post by give.away on 2008-09-25
Hello,

ATI Radeon 2600 HD (Mobile), fglrx , XCFE, Xinerama, internal monitor resolution 1440x900, external (DVI) monitor resolution 1280x1024.

When I start compiz, it stops at:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9581 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap:

```

I read, that because of the dual screen environment the maximal texture size might be exceeded, therefore I commented the texture size check out.
But either way, the above mentioned output is all I get.


I have actually no idea what the problem is.

Thanks in advance,
GA

---

### Post by loomsen on 2008-09-25
Hi.

Did it happen all of a sudden or didn't it work ever since so far? Big difference....As your log shows xgl is either not loaded, or not installed at all.

What does your /etc/X11/xorg.conf look like?

There should be a Section where the modules are specified, which shall be loaded.
Mine for the respective Part says:

```

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

```

Xgl is an basically OpenGL enhanced X-Server.

you can check whats installed by typing
```
 
dpkg -l | grep OpenGL

```
If you miss something here, try installing it prior to editing xorg.conf and other systemfiles if you're unsure. And I recommend to always make a backup if you're going to edit any systemfile. 

To check the configuration of your xorg.conf you can run sth like:
```

cat /etc/X11/xorg.conf

```

You should first check your xorg.conf whether it is configured to use the driver you installed. Then, if so, you should try and add 
Load "glx"
as above to your xorg.conf. 
To avoid rebooting you may drop to a terminal
ctrl+alt+backspace
login
```

sudo /etc/init.d/gdm stop
``` (respectively /etc/init.d/kdm stop if you are running kde)
Now Backup and edit your xorg.conf to add glx, if necessary, with:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
sudo nano /etc/X11/xorg.conf

``` 

Now find the section similar to the one I posted above and add glx, if necessary.

---

### Post by give.away on 2008-09-25
Hello,

thank you.

I have a new xubuntu installation and just tried to get compiz running, so it's kinda "all of sudden" and "didn't work ever since so far" at the same time ;)

Anyway, I understood that XFCE uses AIGLX instead of XGL (but I'm pretty new to this all, so I have no idea if that means anything).
I tried to install XGL but then my X-Server wouldn't start at all (, so I removed it again to have my apart from compiz working environment back).

My xorg.conf looks like this:
```

Section "ServerLayout"
	Identifier     "Dual Screen Layout"
	Screen         "Internal Screen" 0 0
	Screen         "External Screen" RightOf "Internal Screen"
	InputDevice    "Synaptics Touchpad"
	Option	       "Xinerama" "true"
	Option	       "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

# input devices here

Section "Monitor"
	Identifier   "Internal Monitor"
	Option	     "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "External Monitor"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Radeon2600HDM0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Radeon2600HDM1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Internal Screen"
	Device     "Radeon2600HDM0"
	Monitor    "Internal Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "External Screen"
	Device     "Radeon2600HDM1"
	Monitor    "External Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Thanks in advance,
GA

---

### Post by give.away on 2008-09-26
Hello,

the problem seemed to be Xinerama - I could solve it by using BigDesktop. Now Compiz works just fine.

Thanks anyway,
GA

---

