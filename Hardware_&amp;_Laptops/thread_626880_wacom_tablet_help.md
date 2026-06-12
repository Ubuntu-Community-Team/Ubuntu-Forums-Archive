---
title: "wacom tablet help"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by patchido on 2007-11-29
i am trying to install my wacom tablet intuos3 usb with the linux wacom project page but i cant even start the how-to .... it saks me to

```
Unpacking the tarball is usually a one-step process, but I show both steps in case the typical -jxf option doesn't work with tar.

    [jej@ayukawa jej]$ bunzip2 linuxwacom-0.7.8-3.tar.bz2
    [jej@ayukawa jej]$ tar -xf linuxwacom-0.7.8-3.tar
    [jej@ayukawa jej]$ cd linuxwacom-0.7.8-3
```

but when i put the first line this appears 
```
bunzip2 linuxwacom-0.7.8-3.tar.bz2
```

what can i do?

---

### Post by Yellow Pasque on 2007-11-29
You can use the wacom software provided in the Ubuntu repository.
```
sudo apt-get install wacom-kernel-source wacom-tools xserver-xorg-input-wacom
```

Then, you have to uncomment (or add if not there) the following sections in /etc/X11/xorg.conf

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```

and uncomment (or add if not there) the following lines in the ServerLayot section of that file.
```
InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
```

---

