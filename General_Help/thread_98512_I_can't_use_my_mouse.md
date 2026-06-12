---
title: "I can't use my mouse"
date: 2005-12-03
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-03
I've just installed Ubuntu 5.10 in my computer. For some reason, I can't use my mouse. It works perfectly on Windows, but not on Ubuntu.
What should I do to fix it?

---

### Post by 23meg on 2005-12-03
[http://www.ubuntuforums.org/showpost.php?p=524509&postcount=3](http://www.ubuntuforums.org/showpost.php?p=524509&postcount=3)

---

### Post by ubuntuubuntu on 2005-12-04
My mouse is the following:
Serial mouse CLONE 520 DPI - 06055.

---

### Post by xmastree on 2005-12-04
edit your /etc/X11/xorg.conf file.
Find this section:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Change 	Option	"Device"	"/dev/input/mice" 
to 	Option		"Device"		"/dev/ttyS0" 
(that's Szero, not SO)

Change	Option		"Protocol"		"ImPS/2"
to 	Option		"Protocol"		"Microsoft"

Then restart

If that doesn't work, try S1 (port 2)

---

### Post by ubuntuubuntu on 2005-12-16
[QUOTE=xmastree]edit your /etc/X11/xorg.conf file.
Find this section:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Change 	Option	"Device"	"/dev/input/mice" 
to 	Option		"Device"		"/dev/ttyS0" 
(that's Szero, not SO)

Change	Option		"Protocol"		"ImPS/2"
to 	Option		"Protocol"		"Microsoft"

Then restart

If that doesn't work, try S1 (port 2)[/QUOTE]

Please teach me how to it without using the mouse. I don't even know how to open the file.

---

### Post by codejunkie on 2005-12-16
alt+F2 will open the run box then enter this command
```
sudo gedit /etc/X11/xorg.conf
```if it asks for a password enter the password edit the file and then press ```
alt+f
``` then s for save then ```
alt+f 
```and c for close gedit.

---

### Post by ubuntuubuntu on 2005-12-16
[QUOTE=codejunkie]alt+F2 will open the run box then enter this command
```
sudo gedit /etc/X11/xorg.conf
```if it asks for a password enter the password edit the file and then press ```
alt+f
``` then s for save then ```
alt+f 
```and c for close gedit.[/QUOTE]

For some reason, when I type sudo gedit /etc/X11/xorg.conf in the run box and press enter, the run box is closed and the computer doesn't do anything. What should I do?

---

### Post by codejunkie on 2005-12-16
try running the command through the terminal press alt+F2 and type gnome-terminal hit enter when the terminal opens run the above command in it.

---

### Post by ubuntuubuntu on 2005-12-17
And if I now want to change to a USB mouse? What should I do?

---

### Post by xmastree on 2005-12-17
Well, that section I posted earlier is from my xorg.conf and I have a usb mouse. So if yours looks like that it might just work.

---

