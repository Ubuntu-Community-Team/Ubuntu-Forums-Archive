---
title: "ATI Problems"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by p47 on 2006-03-26
Hello I've some problems with ATI Driver now is ok but is very low.

I have a kernel 2.6.16 and I styped apt-get install xorg-driver-fglrx and all is ok. but the interface is very low when I was configured with dpgk-reconfigure xserver-xorg I choose a fglrx driver but is low
My configuration is this :

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X600 (X600SE)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        254000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "DELL 1907FP"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

```

Somebody can help me ?

---

### Post by gmc on 2006-03-27
Hi p47,

[QUOTE=p47]Hello I've some problems with ATI Driver now is ok but is very low.

I have a kernel 2.6.16 and I styped apt-get install xorg-driver-fglrx and all is ok. but the interface is very low when I was configured with dpgk-reconfigure xserver-xorg I choose a fglrx driver but is low
My configuration is this :

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X600 (X600SE)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        254000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "DELL 1907FP"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

```

Somebody can help me ?[/QUOTE]

I don't have an X600, but I'll see if I can help. What do you mean by 'low' and two things about you're configuration above. (1) I don't think you want to be using the Framebuffer, try changing that the false. (2) You shouldn't have to specify the amount of videoram it's autodetected, so comment that out with a #.

G.

---

### Post by p47 on 2006-03-27
Hello ! jo sorry my english is very bad "slow" not low sorry ok :

Now I have vesa driver, but I want the correct driver for my ATI but I dont Know how I can install the driver I'm a new user ubuntu.

Can you help me ?
I have X600 Radeon (X600SE)

---

### Post by RoboJ1M on 2006-03-28
There is a very good guide in the HOW TO forum, you can used the advanced search to find it (sorry, don't have the link to hand)

It's a good step by step on how to uninstall the breezy drivers and get the very latest ATI drivers (which seem to be quite improved, especially for people having the Mesa problem)

J1M.

---

### Post by Zooropa on 2006-03-28
I tried the "HOWTO", and it seemed to put duplicate information in the conf file?

I have an AGP x800VE.

Here is what i have, any help would be appreiciated.
It works, but I'm not convinced - I think it's still using the VESA driver.

Section "Monitor"
	Identifier   "NEC CI A727"
	HorizSync    28.0 - 49.0
	VertRefresh  43.0 - 72.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "NEC CI A727"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


To me, it looks like there are two setups here, one for the VESA, and one for the ATI?

---

### Post by Teroedni on 2006-03-28
To Zooropa


This is what you should use


```
Section "Monitor"
Identifier "NEC CI A727"
HorizSync 28.0 - 49.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection


Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Graphics Adapter 0"
Monitor "NEC CI A727"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection


```







If anything goes wrong this command comes in handy
```
sudo dpkg-reconfigure xserver-xorg
```

It will make sure you cant get back to grapical if the fglrx driver dont work:)

---

### Post by Zooropa on 2006-03-28
Excellent, thanks.

I suspected that's what was wrong, I'll give it a bash when I get home.

I can always sudo dpkg-recongigure xserver-xorg and go back to Vesa if it dies on me!

This is the first Linux problem I've reallly had a look at and tried to get to grips with.
It's starting to make sense.

Should the BUS still be PCI, even with an AGP card?

---

### Post by Teroedni on 2006-03-28
if you mean this

```
BusID "PCI:1:0:0"
```


its only a adress pointer

eg pci PCI:1:0:0 is the same as the agp :)

---

### Post by Zooropa on 2006-03-28
Thanks again, thats another little query put to rest :)

---

