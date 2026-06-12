---
title: "Disabling touchpad tap clikcing"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Death_Sargent on 2007-05-09
I have been trying to disable the option where touching the touch pad a certain way renders a click. 

i installed gsynaptics but now i get this error

[IMG]http://sc922.com/gs.png[/IMG]

How do i do what its telling me to do?

---

### Post by obviouslyshane on 2007-05-09
When i first started using Ubuntu, I was getting really annoyed because i couldn't disable tap to click.  I am assuming that you are talking about the tap to click function, I disabled it by doing the following:

open the terminal and type:

> sudo gedit /etc/X11/xorg.conf

Scroll down and you will find a line that says Synaptics Touchpad, add the following:

> Option "MaxTapTime" "0"

It should look like this now:

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime" "0"
EndSection

Save it, and you may or may not have to reboot.


I hope that helps.

- S H A N E

---

### Post by Death_Sargent on 2007-05-09
that did the trick however it would be nice to find a way to use those gui applications

---

### Post by Yettie on 2007-05-13
> **Death_Sargent said:**
> I have been trying to disable the option where touching the touch pad a certain way renders a click. 

i installed gsynaptics but now i get this error

[IMG]http://sc922.com/gs.png[/IMG]

How do i do what its telling me to do?


I have just found the answer to this one.

Open a terminal and type in
"gksudo gedit /etc/X11/xorg.conf".

In the window which opens, scroll down until you find a section which looks like this,

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "true"
EndSection

If the line   ' Option     "SHMConfig"      "true" ' is missing or looks different, edit it to look like this, then save the changes and you should be able to use the GUI. You may have to restart first.

---

### Post by ucsblaw on 2007-06-01
so I added this line and rebooted and my xserver crashed. I have no idea what to do now. I dont know much about code and linux...im a total noob so i really need some guidance. 

Now, when i boot up ubuntu i get a blue xsever screen and it gives me an error about my graphical interface. I dont know what to do now.

I am running wubi on xp. I had everything working...my nvidia video card, beryl, all that good stuff...i just wanted to get rid of the tapping option on the touchpad and now I think i might have to reinstall.......please someone tell me i dont have to reinstall anything and that i could fix it.

I dont know if this makes a difference but I was running an xgl session

again, i would appreciate any help

> **obviouslyshane said:**
> When i first started using Ubuntu, I was getting really annoyed because i couldn't disable tap to click.  I am assuming that you are talking about the tap to click function, I disabled it by doing the following:

open the terminal and type:



Scroll down and you will find a line that says Synaptics Touchpad, add the following:



It should look like this now:



Save it, and you may or may not have to reboot.


I hope that helps.

- S H A N E

---

### Post by ucsblaw on 2007-06-01
This is what is says when the xserver comes up...in case this makes a difference. I guess the line i entered is not correct...but how do i get rid of it so my computer boots again? Is there any way to boot up in safe mode like we could with xp 


parse error on line 69 of section Inp in file /etc/x11/xorg.conf

Inp is not a valid section name
(EE)problem parsing the config file
(EE)error parsing the config file

fatal server error:
 no screens found

---

### Post by ucsblaw on 2007-06-02
i'm really hurtin here...anyone with some info will save me. I just realized that i could have made a backup of my xorg but i never did....live and learn. 

So, anyway i could get rid of that line?

---

### Post by ucsblaw on 2007-06-02
nevermind...i accidentally deleted a part of my xorg.

I got in using nano /etc/X11/xorg.conf

best

---

### Post by ucsblaw on 2007-06-16
so as you can see from the posts above I had disabled my touchpad 2 weeks ago. It was working great until i screwed things up. I installed ubuntu studio on feisty and it messed up my xserver. So, I finally got all that working...and now I cant disable my touchpad again. 

I know i need to have this section in my xorg.conf but it's not there anymore. 

> Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "MaxTapTime" "0"
EndSection


this is all i have showing in my xorg....i no longer have a synaptics touchpad...but my touchpad works...i just can't disable it. Would it screw things up if i just added this to my xorg? Im afraid to mess with it.

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 50.0
    VertRefresh     0.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x800 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


---

### Post by ucsblaw on 2007-06-17
anyone?

---

### Post by kerry_s on 2007-06-17
nope just add it. but why don't you just make it do what you want?

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"RBCornerButton"	"2"
	Option		"LockedDrags"	"true"
	Option		"Emulate3Buttons"	"true"
	Option		"MaxTapTime"	"110"
	Option		"MaxTapMove"	"300"
	Option		"MaxDoubleTapTime"	"110"
	Option		"ClickTime"	"200"
	Option		"AccelFactor"	"0.050"
EndSection

```

---

### Post by ucsblaw on 2007-06-18
hey thanks for the reply...i tried what you suggested but my touchpad is still not disabled. I also tried the suggestion in the earlier posts and nothing happens. I added it to my xorg and it doesnt seem to have an effect...any suggestions?

I really need to disable the double click on this touchpad

---

