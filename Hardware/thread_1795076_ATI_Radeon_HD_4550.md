---
title: "ATI Radeon HD 4550"
date: 2011-07-02
forum: Hardware
---

### Post by jtomasrl on 2011-07-02
I have a problem with my ATI Radeon HD4550 Card, Im new using linux, starting with ubuntu, BUT the only problem i've got is that I cant change my screen resolution more than 60Hz, At windows I used to set it to 70-75Hz but here I can only up to 60Hz, Im actually using ATI Drivers for linux, ubuntu recommend them at startup.

---

### Post by An Sanct on 2011-07-02
I have the same card (I double-checked)

I also have only 60Hz available, but that is because I use a LCD display. The drivers don't allow values, that might "hurt" your hardware. Besides, 50/60Hz is the standard for a LCD.

---

### Post by jtomasrl on 2011-07-02
I know 50/60Hz its standart for LCD, but im using CRT, 60Hz on CRT is burning up my eyes

---

### Post by cbowman57 on 2011-07-02
Are you able to use the Catalyst Control Center for changing the refresh rate?

---

### Post by jtomasrl on 2011-07-02
I can use ATI CCC but not for changing refresh rate

Xorg.conf



Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

---

### Post by cbowman57 on 2011-07-02
Ok, I'm not using an ATI card so I can't test my own suggestions, or see what you are seeing.  I did google setting refresh rate ati 4550 inux on google and it came back with a couple things.  One of which is to try booting the kernel with noacpi, just press **e** from the grub screen to do that and add it then ctl+x to boot.

The other mentions a **Force** option available via the CCC to force a rate.

Sorry I can't be of more help, hopefully someone that has encountered this problem will pop in with a fix. I know what a PITA it is to have a screen running too low a refresh rate, gets to be hard on the eyes.

---

### Post by jtomasrl on 2011-07-02
someone?

---

### Post by cbowman57 on 2011-07-03
Pop  over to the thread in my signature & pose the question over there.  I think somebody there is likely to have found a solution to this problem.

---

### Post by jocko on 2011-07-03
If you can find the specifications for your monitor, this is a possible solution to your problem:

```
gksudo gedit /etc/X11/xorg.conf
```
In the monitor section and add the refresh and sync ranges:
```
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Q910"
    Option        "DPMS" "true"
[COLOR=Red]    HorizSync    30-110
    VertRefresh  50-150[/COLOR]
EndSection
```
In the screen section, add a display subsection with the modes you want to be able to use:
```
Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
[COLOR=Red]    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes        "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection[/COLOR]
EndSection
```
This worked for me to be able to use the highest supported refresh rate when I still had an ati card and a crt monitor a few years ago.

---

### Post by jtomasrl on 2011-07-03
my xorg.conf dont even have a

Section "Screen"

---

### Post by jocko on 2011-07-03
> **jtomasrl said:**
> my xorg.conf dont even have a

Section "Screen"
It's probably enough to just make the changes to the monitor section.

Edit:
What does your xorg.conf look like?

---

### Post by jtomasrl on 2011-07-03
> **jocko said:**
> It's probably enough to just make the changes to the monitor section.

Edit:
What does your xorg.conf look like?

[http://ubuntuforums.org/showpost.php?p=11005080&postcount=5](http://ubuntuforums.org/showpost.php?p=11005080&postcount=5)

---

### Post by jocko on 2011-07-03
> **jtomasrl said:**
> [http://ubuntuforums.org/showpost.php?p=11005080&postcount=5](http://ubuntuforums.org/showpost.php?p=11005080&postcount=5)
Hmmm... Since it did not look complete, I thought that was only part of it...

Try this:
1. Backup your current xorg.conf:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.con.bak 
```
2. Make a new xorg.conf:
```
sudo aticonfig --force --initial
```
3. Restart x (Alt+SysRq+K, or log out and back in).

Can you set your refresh rate now?
If not, add your monitor's specs to the monitor section in xorg.conf and try again.
If you don't know exactly what to put where, just post your new xorg.conf and the make and model of your monitor (or the horizontal sync and vertical refresh ranges it supports if you know them).

---

### Post by jtomasrl on 2011-07-03
Didnt work

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
    HorizSync    30-110
    VertRefresh  50-150
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes        "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection
EndSection
```

---

### Post by jocko on 2011-07-04
> **jtomasrl said:**
> Didnt work

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
[COLOR=Red]    HorizSync    30-110
    VertRefresh  50-150[/COLOR]
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
[COLOR=Black]        Modes        "1600x1200" "1280x1024" "1152x864" "1024x768"[/COLOR]
    EndSubSection
EndSection
```
Are those refresh and sync rates from your monitor's specs, or did you just copy-paste mine? Note that if you get the driver to use those values, and they are NOT the correct ones for your monitor you may end up with an "out of sync" monitor, which will either just turn it off or in worst case even damage it.

I found something else that could help:
First, you may need to disable xrandr to let the driver take control of the refresh rates:
Add this to the "device" section in xorg.conf:
```
Option      "EnableRandR12" "false"
```

The fglrx driver by some reason saves it's settings in  /etc/ati/amdpcsdb, and those settings will override those in xorg.conf. To get the settings in xorg.conf to stick, you have to run this:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

---

