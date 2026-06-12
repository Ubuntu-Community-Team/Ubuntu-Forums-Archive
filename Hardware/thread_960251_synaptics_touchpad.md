---
title: "synaptics touchpad"
date: 2008-10-27
forum: Hardware
---

### Post by johanhartman on 2008-10-27
Hi all,

I have hardy on a toshiba laptop. The problem I'm having is that the synaptics touchpad on the laptop only works on very basic level (move and click), I don't have any of the extra features eg. scrolling, dragging etc..

To fix this I installed gsynaptics but when I start it, it says "SHMConfig" should be set to "true" in xorg.conf. I checked this but found no option for SHMConfig in the relevant section, so I added it as "true", however gsynaptics still thinks otherwise when I try to start it - even after a restart.

What other options do I have to configure my touchpad, or how can I get gsynaptics to work?

---

### Post by kempo on 2008-10-27
Not exactly an answer to your question... but all the same...

I have a synaptics touchpad. It worked straight away without any further configuration on 8.10 Intrepid Ibex... maybe wait a few days for the final release and see if that solves it? Or install the release candidate...

Hope that helps

---

### Post by johanhartman on 2008-10-27
yeah I guess, but how stable can I expect the final release to be?

---

### Post by sergiom99 on 2008-10-27
this is what I have in my /etc/X11/xorg.conf
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"     "on"
EndSection
 
```

---

### Post by johanhartman on 2008-10-28
> **sergiom99 said:**
> this is what I have in my /etc/X11/xorg.conf
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"     "on"
EndSection
 
```

Yeah, mine's the same. gsynaptics still refuses to start.

---

### Post by sergiom99 on 2008-10-28
please note that SHMConfig is set to 'on' and not 'true' as in your first post.

---

### Post by johanhartman on 2008-10-28
> **sergiom99 said:**
> please note that SHMConfig is set to 'on' and not 'true' as in your first post.

noted, I tried both.

Here's my xorg.conf (is the server layout sections correct?);
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Option		"SHMConfig"		"on"
EndSection

Section "InputDevice"
         Identifier "aiptek"
         Driver "wacom"
         Option "Device" "/dev/input/aiptek"
         Option "Type"   "stylus"
         Option "USB"    "on"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"aiptek"	"SendCoreEvents"
#	Inputdevice	"stylus"	"SendCoreEvents"
#	Inputdevice	"cursor"	"SendCoreEvents"
#	Inputdevice	"eraser"	"SendCoreEvents"
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

---

### Post by sergiom99 on 2008-10-29
i'll check back when i get home to my laptop and post the whole file.

---

### Post by sergiom99 on 2008-10-29
my whole xorg.conf file:

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"     "on"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
sergio@kubuntu:~$                                                                         

Also, check this guy's post> [http://ubuntuforums.org/showthread.php?t=962605](http://ubuntuforums.org/showthread.php?t=962605)

---

### Post by johanhartman on 2008-10-30
> installing xorg-server-input-synaptics resolved the issue.
Thanks
Sri

I already have that installed, but going through their troubleshooter it seems my X conf might not be set up properly for it to work... maybe. Either way my understanding of their guide is not good enough for me to be able to fix the issue as I am not that advanced yet.

[Here's the troubleshooter,]("http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt") and [here's their homepage]("http://web.telia.com/~u89404340/touchpad/index.html")

If someone would be so kind as to look through it and help me fix the problems, that would be very greatly appreciated. But would it perhaps be worth it to try merging the two server-layout sections in my xorg.conf as the bottom one seems rather redundant except for the synaptics bit.

So that I will end up with, e.g.;
> Section "ServerLayout"
	Identifier	"Default Layout"
        screen          "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
        InputDevice	"Synaptics Touchpad"
	Inputdevice	"aiptek"	"SendCoreEvents"
#	Inputdevice	"stylus"	"SendCoreEvents"
#	Inputdevice	"cursor"	"SendCoreEvents"
#	Inputdevice	"eraser"	"SendCoreEvents"
EndSection


---

### Post by sergiom99 on 2008-10-30
well, thats pretty much out of my reach too.
But I do can tell you to make sure you copy your xorg.conf before editing and messing with it.
```
sudo cp /etc/X11/xorg.conf ~/xorg.conf.bak 
```

good luck!

---

### Post by johanhartman on 2008-10-31
I've made a new post in General Help about my xorg.conf file if you're still intersested in following the topic. [link]("http://ubuntuforums.org/showthread.php?p=6070988#post6070988")

---

