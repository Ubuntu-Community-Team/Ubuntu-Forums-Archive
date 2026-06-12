---
title: "Installing tp-scroll on thinkpad?"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by powderific on 2005-02-22
I've been trying to get the scroll button on my R51 to work with tp-scroll and have been having some trouble.  I followed the instructions that are with the file and used other instructions for setting up the rc.local equivalent file as well as the X86Config-4 file and only succeeded in losing all mouse control once I enabled the changes in the X86 config file.  I had a backup so it was no big problem but I'm having some trouble figuring it out.  Has anyone set this up successfully?  If someone could just let me know how they set it up i would greatly appreciate it.

---

### Post by peletiah on 2005-09-09
in case someone else is looking for a solution as well, here it is:
while i couldn't do "make" for the tp-scroll installation(missing files, maybe someone else can tell me what i have to install) i compiled it on one of my gentoo-machines and copied the binary over to the ubuntu-laptop(/usr/sbin/tp-scroll). then i made a bash-script:```
#!/bin/bash
mkfifo /dev/imouse
/usr/sbin/tp-scroll -i /dev/input/mice /dev/imouse &
```
and added in /etc/init.d/xorg-common right after the first two lines
```
/usr/sbin/tpscroll
```

of course you have to do chmod 740 on the tpscroll-script and tp-scroll

in xorg.conf you have to edit the mouse-device section as follows:
```
Section "InputDevice"
             Identifier "Configured Mouse"
             Driver     "mouse"
             Option    "CorePointer"
             Option    "Device"                "/dev/imouse"
             Option    "Protocol"              "ExplorerPS/2"
             Option    "ZAxisMapping"     "4 5"
EndSection
```


est voila, you can scroll and use the middle button to click(e.g. to open links in new tabs in firefox). be sure not to touch the trackpoint when using the middle-click-function as tp-scroll will not recognize it.) :)

---

### Post by kjempe on 2006-01-12
If you don`t need the copy/paste-function of your middle-key, you could insert the following in your xorg.conf to configure the mouse:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option 		"EmulateWheel" 		"on"
	Option 		"EmulateWheelButton" 	"2"
	Option		"XAxisMapping"		"6 7"
	Option		"YAxisMapping"		"4 5"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
Now you just have to restart your X-server and you can use the middle-key as a scrolling wheel. I got the instructions from [http://www.sstuhr.dk/linuxtip/tip1.html]("http://www.sstuhr.dk/linuxtip/tip1.html") and felt free enough to extract the important information. ;)

---

### Post by tedrogers on 2006-11-07
This works well for me.

Except....how do I stop the 3rd button from being a select/click button?? The reason I ask is that when I scroll down a webpage and I happen to cross a link, my browser jumps to that page because the 3rd button is selecting it.

Any ideas?

EDIT:-

Found another solution that stops the 3rd button from acting weird when it crosses over a link on a webpage:

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ImPS/2"
        Option "Emulate3Buttons" "true"
        Option "ZAxisMapping" "4 5"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "2"
EndSection

This also stops the copy and paste function of the 3rd button on my T22, but I never use that anyway.

---

