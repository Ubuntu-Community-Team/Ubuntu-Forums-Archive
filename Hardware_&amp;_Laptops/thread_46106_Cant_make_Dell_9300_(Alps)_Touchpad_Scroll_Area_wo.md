---
title: "Cant make Dell 9300 (Alps) Touchpad Scroll Area work."
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Zerileous on 2005-07-03
Ok, I have the Synaptics 0.14.2 driver installed and no dice.  I am using the xorg.conf from [here](http://rtr.ca/dell_i9300/).  This person has the toucpad working and everything, but it wont for me.  I will show you guys the relevant portions of my xorg.conf file.
```

...

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"synaptics"
EndSection

...

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
          Driver  	"synaptics"
  	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"MaxDoubleTapTime"	"180"
	Option		"ClickTime"		"100"
	Option		"FastTaps"		"1"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"25"
	Option		"MinSpeed"		"0.2"
	Option		"MaxSpeed"		"2.5"
	Option		"AccelFactor"		"0.06"
	Option		"EdgeMotionMinZ"	"30"
	Option		"EdgeMotionMaxZ"	"160"
	Option		"EdgeMotionMinSpeed"	"15"
	Option		"EdgeMotionMaxSpeed"	"15"
	Option		"EdgeMotionUseAlways"	"0"
	Option		"UpDownScrolling"	"1"
	Option		"TouchpadOff"		"0"
	Option		"GuestMouseOff"		"1"
	Option		"LockedDrags"		"1"
	Option		"RTCornerButton"	"2"
	Option		"RBCornerButton"	"2"
	Option		"LTCornerButton"	"2"
	Option		"LBCornerButton"	"2"
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"2"
	Option		"TapButton3"		"3"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option		"CircularPad"		"0"
	Option		"PalmDetect"		"1"
	Option		"PalmMinWidth"		"10"
	Option		"PalmMinZ"		"200"
	Option		"CoastingSpeed"		"0"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"	
	InputDevice	"Synaptics Touchpad"	
EndSection

...
```

I am pretty new to linux, I rean FC1 back when it was all that was out, but never learned a whole lot, just a few basic CLI stuff.  So now I am trying to get ubuntu setup and this is one of my biggest issues.  Everything but the side scrolling works.  And the name for the touchpad has not been changed to go with the website, but everything else has.

---

### Post by mlord on 2005-07-03
I just now have updated my xorg.conf file, and also updated the instructions for getting the Alps Touchpad to work fully with scrollbars.  The updated instructions and files are at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

In short, you must first upgrade the kernel to 2.6.12.2, which now includes the alps kernel driver, and then you must upgrade the synaptics toolkit to 0.14.2 to get a working synaptics_drv.o X11 driver (separate from the kernel driver) and synclient program etc..

I have included a quick link for just the synaptics_drv.o file if you want to try that out first, before grabbing and compiling the whole package.  It won't work unless you upgrade the kernel first, though.

Cheers

---

### Post by jc3835 on 2005-07-03
[QUOTE=mlord]I just now have updated my xorg.conf file, and also updated the instructions for getting the Alps Touchpad to work fully with scrollbars.  The updated instructions and files are at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

In short, you must first upgrade the kernel to 2.6.12.2, which now includes the alps kernel driver, and then you must upgrade the synaptics toolkit to 0.14.2 to get a working synaptics_drv.o X11 driver (separate from the kernel driver) and synclient program etc..

I have included a quick link for just the synaptics_drv.o file if you want to try that out first, before grabbing and compiling the whole package.  It won't work unless you upgrade the kernel first, though.

Cheers[/QUOTE]
 
Is it absolutely necessary to upgrade to the 2.6.12.2 kernel? Is that kernel stable and whatnot?
Great work on your link and help guides!

---

### Post by jc3835 on 2005-07-03
[QUOTE=jc3835]Is it absolutely necessary to upgrade to the 2.6.12.2 kernel? Is that kernel stable and whatnot?
Great work on your link and help guides![/QUOTE]
 Also... which repositories are necessary to get that kernel? 
I notice it does not show up using the standard repositories.
Thanks.

---

### Post by Zerileous on 2005-07-03
Ok, how do I find out what my kernel version is, and how do I upgrade it?
Sorry I am really new at this.

---

### Post by ::DoGG:: on 2005-07-04
To  find out your kernel version type "uname -r" ot just "uname" on the shell ( commandline), to upggrade to a new kernel you have two ways - compiling from source and apt-get a precompiled kernel image. If You new at this i would suggest to just installed precompiled one, do it through synaptics, On the default installation you have an update wizard which makes ver easy for You to upgrade just by simple couple clicks, if the update is available You will see red circle on the upper right top of the screen. When You click it you will se the available updates, you can choose the one you want and and click "Update" button - simple as that.
Hope that helps.

---

### Post by Zerileous on 2005-07-04
Ok my kernel is 2.6.10-5-386.  DoGG, Sorry but I really dont quite understand, I have the ubdate wizard and have run it before but I do not see it now.  Also, running sudo apt-get upgrade doesnt update my kernel.  Is there some way I can just do it through the CLI with apt?  I tried sudo apt-get install kernel-2.6.12.2 but that didnt work...

---

### Post by mlord on 2005-07-04
[QUOTE=jc3835]Is it absolutely necessary to upgrade to the 2.6.12.2 kernel? Is that kernel stable and whatnot?
Great work on your link and help guides![/QUOTE]

It is not strictly necessary to upgrade to 2.6.12(.2), but that is the latest kernel and has a number of bugfixes and the like.  More importantly, it has the alps touchpad driver built-in.

Standard linux kernels are available at [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

But you can instead get the source code for the Ubuntu kernel, and then patch in the alps touchpad driver (source for that is in the synaptics-0.14.2 package), and then rebuild that kernel.

Either way it requires a kernel rebuild / install, rather than a simple point-and-click package install.

Perhaps somebody out there with know-how and bandwidth could grab 2.6.12.2, and apply the patches I have for it ([http://rtr.ca/dell_i9300/kernel](http://rtr.ca/dell_i9300/kernel)) and then make a binary Ubuntu kernel package available for the non-programmers here?

I'm a (kernel) programmer, but I'm not familiar with creating Ubuntu packages.

Cheers

---

### Post by Zerileous on 2005-07-04
[QUOTE=mlord]It is not strictly necessary to upgrade to 2.6.12(.2), but that is the latest kernel and has a number of bugfixes and the like.  More importantly, it has the alps touchpad driver built-in.

Standard linux kernels are available at [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

But you can instead get the source code for the Ubuntu kernel, and then patch in the alps touchpad driver (source for that is in the synaptics-0.14.2 package), and then rebuild that kernel.

Either way it requires a kernel rebuild / install, rather than a simple point-and-click package install.

Perhaps somebody out there with know-how and bandwidth could grab 2.6.12.2, and apply the patches I have for it ([http://rtr.ca/dell_i9300/kernel](http://rtr.ca/dell_i9300/kernel)) and then make a binary Ubuntu kernel package available for the non-programmers here?

I'm a (kernel) programmer, but I'm not familiar with creating Ubuntu packages.

Cheers[/QUOTE]
 so will the alps work automatically with the new kernel?

---

