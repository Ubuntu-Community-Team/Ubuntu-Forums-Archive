---
title: "How do i disable trackpad tapping?"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by justinflavin on 2005-04-17
Since upgrading from Warty to Hoary , the trackpad on my Dell Inspiron 7000 seems to ave taken on a life of its own - i suspect horrible "mouse gestures" or something like that are involved. And trackpad tapping (i.e. tap the trackpad to do something) is enabled , which is really annoying.

how do i disable trackpad tapping in Gnome? there doesnt appear to be an option in the mouse config..

---

### Post by malmjako on 2005-04-18
Have a look at /usr/share/doc/xorg-driver-synaptics/README.gz! It contains all the settings you can make.

Excerpt: > If you set MaxTapTime=0 then the touchpad will not use tapping at all, i.e. touching/tapping will not be taken as a mouse click.
This is done in /etc/X11/xorg.conf in the "InputDevice" section with Driver "synaptics". My such section looks like this:```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option                  "LockedDrags"           "on"
        Option                  "SHMConfig"                     "on"
        Option                  "RTCornerButton"        "1"
        Option                  "RBCornerButton"        "1"
        Option                  "CircularScrolling"     "on"
        Option                  "CircScrollTrigger"     "2"
        Option                  "EdgeMotionMinSpeed"            "0"
        Option                  "EdgeMotionMaxSpeed"            "0"
EndSection
```
You would add```
Option "MaxTapTime" "0"
``` to disable trackpad tapping.

---

### Post by anando on 2005-04-18
Don't you need to load the 'Synaptics' module as well in the 'Modul' section of /etc/X11/xorg.conf ?

---

### Post by malmjako on 2005-04-20
[QUOTE=anando]Don't you need to load the 'Synaptics' module as well in the 'Modul' section of /etc/X11/xorg.conf ?[/QUOTE]
Nope. I don't have it listed in my xorg.conf and the touchpad is working just fine. This is on a HP Omnibook 6000.

---

### Post by mendicant on 2005-04-20
[QUOTE=anando]Don't you need to load the 'Synaptics' module as well in the 'Modul' section of /etc/X11/xorg.conf ?[/QUOTE]

You just need the ServerLayout that is actually in use to reference the correct mouse section.

---

### Post by anando on 2005-04-21
[QUOTE=mendicant]You just need the ServerLayout that is actually in use to reference the correct mouse section.[/QUOTE]

So .... can you please help - I have the following in my xorg.conf - what changes do I need to make ? 

I have synaptics in my ServerLayout, and I also have "TapButton1" set to "0". Still it does not work for me  :| 

Please help - I am not an expert.

- Anando.

------------------------------------------------------------------------------------------------------------------------
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

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
	#Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
	#### Anand adding ...
	Option		"SHMConfig"		"on"
	#Option		"MaxTapTime"		"0"
	Option		"TapButton1"		"0"
	####
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	#InputDevice	"Configured Mouse"	"SendCoreEvents"
	#InputDevice	"Synaptics Touchpad"	"CorePointer"
	InputDevice	"Configured Mouse"	
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by mendicant on 2005-04-21
I assume you're trying to disable tap-to-click behavior.  Does the touchpad work at all?  Are you sure you have a synaptics touch pad?  Is it an Alps touchpad maybe?  What's the output of /var/log/Xorg.0.log?  You should see something like the following (one of them):

(--) Configured Mouse synaptics touchpad found

(--) Configured Mouse ALPS touchpad found

---

### Post by anando on 2005-04-21
[QUOTE=mendicant]I assume you're trying to disable tap-to-click behavior.  Does the touchpad work at all?  Are you sure you have a synaptics touch pad?  Is it an Alps touchpad maybe?  What's the output of /var/log/Xorg.0.log?  You should see something like the following (one of them):

(--) Configured Mouse synaptics touchpad found

(--) Configured Mouse ALPS touchpad found[/QUOTE]

Hi - many thanks for taking a look. The touchpad definitely works - and that is why I want to disable the tap-to-click behavior !

I took a look at the Xorg.0.log and could not find the lines above. In fact the only lines that refer to the mouse or the touch pad are appended below. So ... what do you think - and what should I do to get the taping to stop. BTW I have a Dell Latitude 600.

---------------------------
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by mendicant on 2005-04-21
Perhaps you have an alps touchpad.  Have you tried recompiling your kernel with the alps patch:

[http://ubuntuforums.org/showthread.php?t=28132&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=28132&page=1&pp=10)

You can check first if you have an Alps touchpad.  The Dell documentation might say.

---

### Post by anando on 2005-04-22
[QUOTE=mendicant]Perhaps you have an alps touchpad.  Have you tried recompiling your kernel with the alps patch:

[http://ubuntuforums.org/showthread.php?t=27650&goto=newpost](http://ubuntuforums.org/showthread.php?t=27650&goto=newpost)

You can check first if you have an Alps touchpad.  The Dell documentation might say.[/QUOTE]

Many thanks for the suggestion - I have recompiled 2.6.10 kernel with the alps patch and now the touchpad problem has gone. 

BTW, may I request you to put up a 'good' example of xorg.conf such that the touchpad parameters are optimised - I know it depends on the hardware, but some starting point for fiddling around with the parameters would be quite useful.

- Anando.

---

### Post by mendicant on 2005-04-22
Well, I didn't do that because I mention the document that already contains that information.  I'm also not sure what there is to optimise, besides the common disabling of the click-on-tap behavior, which the document mentions (or one of the docs under the /usr/share/doc/xorg-driver-synaptics directory), and which I mentioned again in the howto.

---

### Post by dickohead on 2005-06-28
ARRGHH!!!!

Thank you guys so much!! That tap/click is the MOST annoying thing about laptops! Thank you all so much for helping me fix it!!!

---

### Post by IngerK on 2005-07-06
I have a Dell latitude D600, and I have installed the alps-kernel as suggested here (and in [http://ubuntuforums.org/showthread.php?t=28132&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=28132&page=1&pp=10) ).

Using the new kernel, the trackpad-problem has gone, but so has my wireless-connection :-(

In /var/log/syslog I get following message:

localhost kernel: ipw2100: eth1: Firmware 'ipw2100-1.3.fw' not available or load failed.

With the "old" kernel the ipw2100 wireless-card works fine, but the trackpad is very annoying and I want to disable it...

Any suggestions?

---

### Post by IngerK on 2005-07-06
Problem solved :-)
I made a symlink ipw2100-1.3.fw -> ipw2100-1.3.fw-2.6.10-5-386 :D

---

### Post by linuxfanatic1024 on 2005-07-12
This is why I bought a mouse for my laptop...  :grin:

I have a Synaptics touchpad and found out that I had to enable "SHMConfig" as mentioned earlier in order to get the configuration to work. If you have Kubuntu, you can install the ksynaptics package and have a nice point-and-click program for configuring this stuff. Here's my xorg.conf Synaptic section:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
EndSection

```

You also may need to put the synaptics module with into the Modules section. I haven't tried this without putting it there.

But I still use my mouse most of the time...  :wink:

---

### Post by milesj on 2005-10-14
Had the same infuriating problem.
particularly with Firefox.

Solved with this :


        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
#	Option		"MaxTapTime"		"0"
	Option		"HorizScrollDelta"	"0"
	Option		"LockedDrags"		"false"
	Option		"CircularScrolling"	"false"
	Option		"SHMConfig"	"on" 

in /etc/X11/XF86Config-4

---

### Post by ptepper on 2005-10-28
For anyone using 5.10 Breezy, you should stop reading this thread and proceed here immediately:

[http://ubuntuforums.org/showthread.php?t=76585]("http://ubuntuforums.org/showthread.php?t=76585")

I've gone through all these steps, they don't work, but those do and it's real quick. 

-paul

(thanks to Chad Glendenin for pointing me to it)

---

### Post by DavidFourer on 2006-05-13
To malmjako
You got my hopes up but the tap feature, which works incorrectly, won't shut off.  I've been trying to get ubuntu breezy to work better on my Dell inspiron 6000 for two months.  I've found the forums extremely detailed but it's too complex.  I even got suspend-to-ram to work!  and occasionally I can watch video.  The display is beautiful, just like in Windows!  And wireless not working.

My cat /proc/bus/input/devices line says 

[COLOR="Blue"]I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

[/COLOR]and my /etc/x11/xorg.config looks like
[COLOR="Blue"]Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection[/COLOR]


Some people have about 20 lines with "Identifier ALPS" 

Should I ad them?

and then change the end lines where it says:
[COLOR="Blue"]Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection 
[/COLOR]to say 
InputDevice "ALPS"

---

