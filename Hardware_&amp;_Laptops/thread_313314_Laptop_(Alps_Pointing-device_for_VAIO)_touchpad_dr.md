---
title: "Laptop (Alps Pointing-device for VAIO) touchpad drivers?"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by ycomp on 2006-12-05
I installed Ubuntu on a Sony VAIO... everything seems to work fine except the touchpad is very sensitive... don't know if that's the right word. 

The touchpad works fine except for 2 things:

1) if I move over something, it might click it. For instance if I move over the icons on the top (firefox, evolution) then one of these programs might be launched

2) the scroll "wheel" aspect of the touch pad doesn't work

Does anyone know if there are any special drivers I need to get? And If so, how to install them.. I'm new at linux. 

I am mostly interested in solving problem #1... problem #2 is a bonus (but greatly appreciated)

---

### Post by shimrah on 2006-12-05
I have a VAIO VGN-FS980 ... my scroll pad works fine without any additional drivers (Dapper). I do, however, experience your first problem. The "sensitivity" extends to a sensitivity to being tapped by some magical/immiterial force, as it happens even when nothing touches it (from time to time). For example, I'll be typing in OOWordProcessor and the cursor will spontaneously jump to the cursor.

Is this perhaps a hardware problem? I have the same problem in XP sometimes (though, admittedly, not as often).

Perhaps there's a way to de-sensitize the touchpad... I'll keep poking around if you do. :)

---

### Post by SendDerek on 2006-12-05
I have Sony Vaio as well (VGN-FE550G) and the touchpad worked pretty well right out of the box granted there were some things that it's still lacking like the "Palm Detection" and "Horizonal Scroll" doesn't always work.  

I don't know if this will work directly to yours, but here's my /etc/X11/xorg.conf file:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

There is a great guide on how to get these synaptic touchpads to work well with linux. I'll go find it.  Be back in a bit...

Oh, and there are mouse options in the System->Preferences->Mouse and if you goto the Motion tab you can find the acceleration and mouse speed options there. Does that help?

---

### Post by ycomp on 2006-12-05
cool thanks, the guide would be very helpful. Mine is a VGN-N130G.

does your scroll "edge" work? (running the finger up and down the right side of the pad)

---

### Post by SendDerek on 2006-12-05
Here is a pretty good documentation of all the functions in the Synaptics touchpad driver:

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

And there are a lot of answers right here on the forums, but I couldn't directly find the one that I was thinking of.

Instead, I found a package called qsynaptics that sounds promising.  I'm going to see what happens.

If you make the changes to the xorg.conf file, remember that you need to restart GDM by ctrl+alt+backspace.

---

### Post by ycomp on 2006-12-05
Great, I'll be sure to try these things out. Thanks.

---

### Post by SendDerek on 2006-12-05
> **ycomp said:**
> cool thanks, the guide would be very helpful. Mine is a VGN-N130G.

does your scroll "edge" work? (running the finger up and down the right side of the pad)

Yeah!  It does work.  It's about the only thing that does work! :-D 

I'm looking into the qsynaptics package right now to find out what we can do with that.  Sounds very promising if we could get it to run.  The requirements so far look like this after running qsynaptics in the terminal:

> 
please install the synaptics touchpad driver!
please enable X shared memory in XF86Config


---

### Post by SendDerek on 2006-12-05
Hey!  Alright, this is cool.  It worked after making some changes to the xorg.conf file and installing some synaptics stuff from the package manager.

Okay, so add this line to the xorg.conf file under the proper category:

```
	
Option    	"SHMConfig"       	"1"

```

Mine looks like this:
```

Section "InputDevice"
	Option    	"SHMConfig"       	"1"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

That should take care of the shared memory issue.

Now, I installed a couple programs at once, so I don't know which on specifically helped and which didn't but when I did a search for synaptic in the package manager, I got a list of a few items.  This is what I have installed:

> 
qsynaptics
synaptic (0.57.8ubuntu)
tpconfig (3.1.3-7)
xserver-xorg-input-synaptics  (0.14.3+seriouslythistime-0ubuntu3)


Now the messages are gone and I'm going to play around.  Lemmie know what you find out!

---

### Post by SendDerek on 2006-12-05
Welp, I did a test run in Open Office Word, but it seems that the palm detection didn't work and the horizontal scroll doesn't work either.  Maybe it's just something I'm doing wrong?  

I'll keep playing and see what evolves.  

I hope this has helped you out.

Update: I just disabled the tap out of it, and it worked.  There is no more tap when I'm writing a paper in word.  So, this is great news for me.  There is a hint of horizontal bar working though.  It will work in opera, not in firefox or openoffice.

---

### Post by Fully216 on 2006-12-05
I have an alps touchpad on a compaq r3000.  I have found that the synaptics touchpad driver works really well.

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

I have added many options to my xorg.conf to give it the feel that I wanted

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
	# Added Options
    Option         "VertScrollDelta" "20"
    Option         "LeftEdge" "120"
    Option         "RightEdge" "830"
    Option         "TopEdge" "120"
    Option         "BottomEdge" "650"
    Option         "FingerLow" "14"
    Option         "FingerHigh" "15"
    Option         "MaxTapTime" "0"
    Option         "MaxTapMove" "110"
    Option         "ClickTime" "0"
    Option         "EmulateMidButtonTime" "75"
    Option         "MinSpeed" "0.4"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.03"
    Option         "EdgeMotionMinSpeed" "200"
    Option         "EdgeMotionMaxSpeed" "200"
    Option         "UpDownScrolling" "1"
    Option         "CircularScrolling" "0"
    Option         "CircScrollDelta" "0.1"
    Option         "CircScrollTrigger" "2"
EndSection

setting clicktime = 0 disables the double click option which drove me crazy.  I used to have the same through scrolling over something and have it magically click on it.  Now I only use the two bottoms below the touchpad to left and right click.  

Hope this helps!

EDIT: note that this driver is used by default in Edgy.  Since you are using dapper, I would strongly recommend the above driver.

---

### Post by SendDerek on 2006-12-05
Thanks for the tip fully!  

I'm assuming that the package is in the package manager and that it's called xfree86-driver-synaptics?  Well, when I installed that it uninstalled ubuntu-desktop.  Is this a problem?

---

### Post by SendDerek on 2006-12-06
Okay, update:

I went ahead and installed the synaptics-0.14.6 by compiling it and following the instructions in the INSTALL.txt file. 

But, still nothing.  It's almost like my changes to the xorg.conf file are being ignored.  

I'm not trying to hijack this thread, but I'm wondering... can somebody help *me* now? :) (Or should I make my own thread?)

Here's a copy of my xorg.conf file:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load    "synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	# Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Option    	"SHMConfig"       	"1"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	# Added Options	
	Option "HorizScrollDelta" "0"
	Option "VertScrollDelta" "20"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "0"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "MinSpeed" "0.4"
	Option "MaxSpeed" "1.0"
	Option "AccelFactor" "0.03"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ycomp on 2006-12-06
no, keep posting here... I haven't been able to look into this yet on my laptop. If I do figure anything out I'll let you know, but I might not get to it until the weekend.

---

### Post by hyperform on 2006-12-06
I had all sorts of problems with getting the ALPS to work right until just recently.  My problem was that it wasn't recognizing it all the time and sometimes I had to wait for X to load, then kill it and let it reload for it to acknowledge the touchpad right.  I had to change the Device to /class/input/input6 and it worked just peachy with gsynaptics (qsynaptics never worked right for me).  Once I did that, everything worked just fine.  Check what your /var/log/messages says that the touchpad is registering on and if possible tell xorg.conf to load specifically from there.

---

### Post by Fully216 on 2006-12-12
You might want to check out your device.  In the top input device section you list something different from the bottom section.  When I pasted mine, I showed 

Option "Device" "/dev/psaux" 

because that is where my mouse is listed.  Each machine will need to have their device changed for their hardware.

Check [http://wiki.x.org/wiki/](http://wiki.x.org/wiki/) for more details.  

evdev is the generic input event interface. It passes the events generated in the kernel since verson 2.6.8 straight to the program, with timestamps. This is the way for X to get keyboard and mouse events. It allows for multihead in X without any specific multihead kernel support.

To see on which device you mouse is mapped, use the following command:

cat /proc/bus/input/devices

pay key attention to the listed input and handlers.

---

### Post by Fully216 on 2006-12-12
There are also GUI configuration untilities to help you.

[http://sourceforge.net/projects/qsynaptics](http://sourceforge.net/projects/qsynaptics)
[http://ltpconf.sourceforge.net/](http://ltpconf.sourceforge.net/)
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

a GKrellM plugin to control the synaptics touchpad can be found here.

[http://perso.wanadoo.es/r_mano/vaio/gksyn.html](http://perso.wanadoo.es/r_mano/vaio/gksyn.html)

Lastly, check out the interface guide for help.

[http://www.synaptics.com/decaf/utilities/ACF126.pdf](http://www.synaptics.com/decaf/utilities/ACF126.pdf)

---

### Post by stenka on 2006-12-14
This is a bug, and hasn't been taken seriously since there are not many bug reports.
Please check here :
[https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540](https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540)

---

### Post by Fully216 on 2006-12-15
Note: that bug applies to edgy (as the problems there are a digression from what worked in Dapper).  If you are a dapper user, then it should not apply to you.  You should be able to get it working with a little bit of tinkering, as is the case with you SendDerek.

---

### Post by eitan_a on 2007-01-01
I have this bug too...will try the input6 and see if it works.  That is what the device is set to now, but as you can see from my message log, it changes :confused: :confused: 

Jan  1 10:11:06 eitan-laptop kernel: [17179586.348000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
Jan  1 10:36:04 eitan-laptop kernel: [17181093.684000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6
Jan  1 16:22:51 eitan-laptop kernel: [17201895.684000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input8
Jan  1 16:23:11 eitan-laptop kernel: [17201918.408000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input10
Jan  1 17:42:54 eitan-laptop kernel: [17179586.376000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
Jan  1 17:43:02 eitan-laptop kernel: [17179601.604000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6

---

