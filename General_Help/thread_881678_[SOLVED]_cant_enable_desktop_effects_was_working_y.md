---
title: "[SOLVED] cant enable desktop effects was working yesterday HELP!....(Intel graphics)"
date: 2008-08-06
forum: General Help
---

### Post by Joey-G on 2008-08-06
Had this all working up until yesterday i think an update may of ruined the settings or something.

i run hardy ubuntu on my toshiba dual core processor laptop 2 gb of RAM

right.... i tried compiz check and compiz into the terminal and here is what i have got:


```

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

```

then i did "compiz" into the terminal and i got this:


```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

i have Xgl installed and Nvidia could be installed aswell but nothing seems to be working according to compiz check. here is the Xorg.config file aswell..........really need some help now it is greatly appreciated..


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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

thanks in advance..

---

### Post by akudewan on 2008-08-06
> **Joey-G said:**
> 

i have Xgl installed and Nvidia could be installed aswell but nothing seems to be working according to compiz check. here is the Xorg.config file aswell..........really need some help now it is greatly appreciated..



If you have an intel graphics card, why install NVidia? Also, can you post your *entire* xorg.conf file ?

---

### Post by Joey-G on 2008-08-06
ok i didnt know if i needed NVidia or not but its not installed anyway.....that was the entire xorg.conf file....was there supposed to be more. 

thanks for your help....

---

### Post by akudewan on 2008-08-06
I'm stumped if that was the entire file. :( You can try running a search of the forum, or maybe someone else can help.

Btw, you don't really need xserver-xgl to get compiz running. Also 'glxgears' should be working. Try running 'glxinfo | grep direct' in a terminal, and see if its saying 'Yes' to direct rendering.

---

### Post by Joey-G on 2008-08-06
thanks for all the help on my two threads i will mark them both as solved. my bad for the swearing in the other thread was extremly annoyed.

got it working again the update installed NVidia and xserver-gl which stopped my desktop effects from working. being new to this i didnt know i didnt need them.

but linux is a learning curve. i just hope hardy becomes a little more stable but i am soo much happier with this than windows. willing to learn new things hit me up if you want i study computers so learning new code comes easy.

many thanks again guys joey-G

---

### Post by overdrank on 2008-08-06
> **Joey-G said:**
> thanks for all the help on my two threads i will mark them both as solved. my bad for the swearing in the other thread was extremly annoyed.

got it working again the update installed NVidia and xserver-gl which stopped my desktop effects from working. being new to this i didnt know i didnt need them.

but linux is a learning curve. i just hope hardy becomes a little more stable but i am soo much happier with this than windows. willing to learn new things hit me up if you want i study computers so learning new code comes easy.

many thanks again guys joey-G

And please do not create multiple threads on the same issue as this can cause even more undue stress . :)

---

