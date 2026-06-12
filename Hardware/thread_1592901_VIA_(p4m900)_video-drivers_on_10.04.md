---
title: "VIA (p4m900) video-drivers on 10.04"
date: 2010-10-11
forum: Hardware
---

### Post by dhamith on 2010-10-11
I've installed [VIA video drivers for linux]("http://linux.via.com.tw/support/downloadFiles.action")  on Ubuntu 10.04. And _after enabling normal or extra visual effects, screen acting really bizarre_. But with low resolution like 1024X768 its working fine. I cant go high resolution. Is there any thing I can do about this or I have to move low resolution or no Visual effects?

@ resolution 1280X1024 with normal visual effects
[IMG]http://img195.imageshack.us/img195/8862/screenshot8nw.png[/IMG]

---

### Post by lord_wenk on 2010-10-11
wow,... i never successfully installed this driver on my Via VN896...
can i see your xorg.conf please???

---

### Post by dhamith on 2010-10-13
> **lord_wenk said:**
> wow,... i never successfully installed this driver on my Via VN896...
can i see your xorg.conf please???

Okay, ---> But i dont think using my xrog.conf will help you. You can download drivers from here ([http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)) choose your OS and your driver. and installation instructions are here ([https://help.ubuntu.com/community/OpenChrome#Beta Drivers for Ubuntu 10.04](https://help.ubuntu.com/community/OpenChrome#Beta Drivers for Ubuntu 10.04)). 

```
Section "ServerLayout"
       Identifier	"Default Layout"
       Screen		"Default Screen"
       InputDevice	"Mouse"
       InputDevice	"Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier	"Keyboard"
       Driver		"kbd"
       Option		"XkbRules"	"xorg"
       Option		"XkbModel"	"pc105"
       Option		"XkbLayout"	"cn"
EndSection

Section "InputDevice"
       Identifier	"Mouse"
       Driver		"mouse"
       Option		"CorePointer"
EndSection

Section "Monitor"
       Identifier	"CRT"
       Option	"Enable"	"true"            
EndSection

Section "Monitor"
       Identifier	"LCD"
       Option	 "Enable"	"false"         
EndSection	

Section "Monitor"
       Identifier	"DVI"
       Option	 "Enable"	"false"
EndSection	

Section "Monitor"
       Identifier	"TV"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"HDMI"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"CRT-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"LCD-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"DVI-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"TV-2"
       Option	  "Ignore"	"true"
EndSection

Section "Device"
	#BusID "PCI:01:00:0"
	Driver 	"via"
	VendorName  	"VIA Tech"
	BoardName   	"via"
	Identifier	"Configured Video Device"
	Option		"MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
              Depth  24
       EndSubSection
       Identifier	"Default Screen"
       Device		"Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
	Option	"Composite"			"Enable"
EndSection
```

---

