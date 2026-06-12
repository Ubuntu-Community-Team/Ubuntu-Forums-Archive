---
title: "[SOLVED] touchpad always active"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by rudedcam on 2008-03-29
It seems impossible for me to find a way to get rid of the touchpad permanently or even better, find a way to turn it on or off at will.

here's a part of my xorg.conf file
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		 "SHMConfig"		 "on"
	Option		"TouchpadOff"		"1"
EndSection

```

[IMG][[img]http://img2.freeimagehosting.net/uploads/th.25bb5c5fbb.jpg[/img]](http://img2.freeimagehosting.net/image.php?25bb5c5fbb.jpg)[/IMG]
[IMG][[img]http://img2.freeimagehosting.net/uploads/th.7a2a8ad884.jpg[/img]](http://img2.freeimagehosting.net/image.php?7a2a8ad884.jpg)[/IMG]

also in terminal:
```
syndaemon -i 3 -t -K
Can't access shared memory area. SHMConfig disabled?

```
```
synclient TouchpadOff=0
Can't access shared memory area. SHMConfig disabled?

```

can somebody please help me?

---

### Post by metol on 2008-03-29
I use a touchpad tool available in synaptic called 'gsynaptics'.

After installation, go to System --> Preferences --> Touchpad

It has many configuration options for the touchpad including the ability to disable it completely.

Hope this helps,
Metol

---

### Post by kneewax on 2008-03-29
This looks just what I need, however when I try to run it I get the following error:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I have looked in my Xorg.conf file and cannot find the SHMConfig property - do you know if I should add it?  If so where in the file?

Thanks

---

### Post by shwick on 2008-03-29
It should look like this:

```
Option		 "SHMConfig"		 "on"
```

and it should be added to the synaptic-touchpad-inputdevice part, here's mine:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
EndSection
```

---

### Post by rudedcam on 2008-03-29
that is very strange, here's my xorg.conf
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		 "SHMConfig"		 "true"
	Option		"TouchpadOff"		"1"
EndSection
``` I've tryed to substitute "true" for "on", still no change.

when i go to system>preferences>touchpad i get this error message: [I]GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
[/I]

---

### Post by shwick on 2008-03-29
Well, the TouchpadOff line should disable your touchpad entirely, and the syndaemon is used to disable it temporarily after a keyboard button is pressed.

Anyway, you can probably find what you need here:
[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

And here's something on how to set it up so you can disable it with a hotkey:
[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey]("https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey")

They both require SHMConfig to work though, and i think it should work without the touchpadoff line

---

### Post by rudedcam on 2008-03-30
i've tryed both documentations but none of the tutorial did the trick. it's unfortunate.

could it be because i have a specific computer? 

keep the help coming, i need it badly

---

### Post by kneewax on 2008-03-30
I added the line 

Option		"SHMConfig"		"true"

to my xorg.conf file as suggested andafter a reboot the gsynaptic app works fine.  Now I can type without fear of scrolling up and editing previous paragraphs  - which is what was happening when I brushed the pad accidental before!

Thanks for the advice guys!

---

### Post by metol on 2008-03-30
As a wild guess, I wonder if the following line in your config file is causing the problem...
```
Option		"TouchpadOff"		"1"
```

I wonder this because it is first telling X to use Gsynaptics to control the touchpad and then it is turned off.  Just a guess though.  Other than that line, your config file looks the same as mine.

Are you still getting an error regarding the SHMConfig setting?  Or is it simply not working?  Are you restarting X after you make these changes to the config file?

---

### Post by rudedcam on 2008-03-30
> **metol said:**
> As a wild guess, I wonder if the following line in your config file is causing the problem...
```
Option		"TouchpadOff"		"1"
```

I wonder this because it is first telling X to use Gsynaptics to control the touchpad and then it is turned off.  Just a guess though.  Other than that line, your config file looks the same as mine.

Are you still getting an error regarding the SHMConfig setting?  Or is it simply not working?  Are you restarting X after you make these changes to the config file?

yes i did try with and without de "option touchpadoff "1""  restarting the X everytime in between but still no effect.

are you suggesting that there might be an orther in which to place them?
could you paste your xorg file completely so i can have a good look at it?

kneewax; good job, i envy you ;)

---

### Post by metol on 2008-03-31
> **rudedcam said:**
> are you suggesting that there might be an orther in which to place them?
could you paste your xorg file completely so i can have a good look at it?

No, I don't think the order should matter.  I was just guessing that these two options may be incompatible but it looks like this is not the case.  I'm not sure what else to suggest.

I'm at work right now and my laptop is at home... I can post my xorg file for you this evening.  Not sure if it will help you are not, but it is worth a try.

---

### Post by metol on 2008-03-31
rudedcam, here is my xorg.conf file that I promised you...

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "Buttons" "7"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
        Option      "Resolution" "800"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
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
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Michl on 2008-03-31
I have the same problem on a Dell C610 and tried all the suggestions available on
this forum and elsewhere.  I think the problem must be related to differences in
laptops because for some people this works and others it just doesn;'t.  I've
been banging my head against this problem for 6 months now without success.

---

### Post by metol on 2008-03-31
> **Michl said:**
> I have the same problem on a Dell C610 and tried all the suggestions available on
this forum and elsewhere.  I think the problem must be related to differences in
laptops because for some people this works and others it just doesn;'t.  I've
been banging my head against this problem for 6 months now without success.

Thank you for sharing your experiences Michl, I think the OP may suffer a similar fate.

I am by no means an expert, but I did a bit more digging and have a few possibilities to suggest.

1) In the top panel under System--> Preferences --> Mouse, I have a tab titled "Touchpad", do you have a similar tab and will that disable the touchpad?  My settings here seem to be ignored but I would assume this is because I'm using SHMConfig.

2) In the xorg.conf file, have you tried removing the touchpad section in addition to the touchpad reference in the bottom of the config file?  Maybe you can just get X to ignore it completely?

3) Can you disable it in the BIOS?

Sorry if these ideas turn out to be dead ends, I wish I had a definitive answer for you rudedcam.

Best of luck,
Metol

---

### Post by bran on 2008-03-31
on several types of laptops there are buttons to turn the touch pad off and on; usually marked with a  finger in a rectangle.  others have a combo mine is Fn+F7

---

### Post by rudedcam on 2008-04-19
sorry for the delay, 

metol: I have tryed the options you gave me without success.
bran: those 2 keys haren't working and i can't get them to work.

this is how i  (a friend of mine) fixed it:

went to /etc/rc.local

and i've inserted this line
```
modprobe -r psmouse
```

my touchpad is now official dead.

---

