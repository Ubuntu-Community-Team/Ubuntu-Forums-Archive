---
title: "Vaio Synaptics problems - Gsynaptics couldn't initialize"
date: 2008-07-27
forum: Hardware
---

### Post by DeanoUK on 2008-07-27
Hi all,

Tried to follow all the instructions on the forums relating to gsynaptics, but still when I go to 'touchpad' it gives me the error:

Gsynaptics couldn't initialize
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


Using 7.04 fyi.
My xorg.conf looks like this:

> 
Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"      	   "100"
	  Option "SHMConfig" 			"on"
	  Option "RightEdge"     	   "1100"
	  Option "TopEdge"       	   "50"
	  Option "BottomEdge"    	   "300"
	  Option "FingerLow"     	   "30"
	  Option "FingerHigh"    	   "40"
	  Option "MaxTapMove"              "100"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "MinSpeed"      	   "0.15"
	  Option "MaxSpeed"      	   "0.90"
	  Option "AccelFactor"   	   "0.10"
	  Option "VertScrollDelta"         "25"
	  Option "HorizScrollDelta"        "30"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	
	InputDevice "Synaptics Touchpad"
EndSection


Thanks for your help in advance.

---

### Post by argosreality on 2008-07-27
I'm pretty sure you need to add the 'SHMConfig' 'true' after the InputDevice "Synaptics Touchpad" but before the endsection

---

### Post by DeanoUK on 2008-07-28
> **argosreality said:**
> I'm pretty sure you need to add the 'SHMConfig' 'true' after the InputDevice "Synaptics Touchpad" but before the endsection

It's in the config I pasted?

---

### Post by klausner on 2009-01-02
> **argosreality said:**
> I'm pretty sure you need to add the 'SHMConfig' 'true' after the InputDevice "Synaptics Touchpad" but before the endsection

I have the line:

[INDENT]Option "SHMConfig" "on"[/INDENT]

in my Xorg.conf. Also tried

[INDENT]Option "SHMConfig" "true"[/INDENT]

and I can't get Gsynaptics to work either. 

Another [thread]("http://ubuntuforums.org/showthread.php?t=526459&highlight=GSynaptics+couldn%27t+initialize") suggested I needed to add 

[INDENT]InputDevice "touchpad" "AlwaysCore"[/INDENT]

to the Section "ServerLayout". Since I didn't have such a section, I created one, complete with the EndSection, but that completely broke X and I had to remove it to get back to my starting point.

If it makes a difference, I'm running 8.10.

---

### Post by MockY on 2009-07-07
I'm in the same boat

---

### Post by metrofun on 2010-02-03
I have the same issue

---

### Post by nicoArg on 2010-05-19
Me too. Please help.

---

### Post by mxvmp on 2010-10-08
This might be the first time I haven't found my answer searching the forums and googleing. 
I have a Dell Latitude E6410, with Ubuntu 10.04 and it seems I can't enable the scrolling in the touchpad. 
I get the error "GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics" and tried all the above and have not managed to solve this issue.
will someone please point us to the right direction?

---

### Post by gotamangoflavouredrat on 2011-04-30
word to the wise do not use the suggestion found here [http://forums.debian.net/viewtopic.php?f=5&t=37530](http://forums.debian.net/viewtopic.php?f=5&t=37530)

Will lead to to an unbootable system. To fix this press shift while booting , then choose the recovery mode in the grub menu... click on the options that lead towards to low graphics boot mode. then edit /etc/X11/xorg.conf and remove any changes made.

Tried what OP said still cannot fix the touchpad issue on this vaio VPCYB15AG. 

Can scroll down, cannot scroll up. And the famous 
```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

---

