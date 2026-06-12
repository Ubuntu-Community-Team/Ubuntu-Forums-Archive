---
title: "Right click not working on tablet X200T"
date: 2009-04-21
forum: Hardware
---

### Post by nimonika on 2009-04-21
I have successfully installed ubuntu on my tablet however the right click does not seem to work. Here are the contents of my xorg.conf. Please could someone advise on what changes I need to make enable right click.

 # Uncomment the following section if you you have a TabletPC that upports touch

Section "Monitor"
	Identifier    "Configured Monitor"
EndSection

Section "Monitor"
	Identifier    "HDMI-1"
	Option        "Ignore" "True"
EndSection

Section "Monitor"
	Identifier    "HDMI-2"
	Option        "Ignore" "True"
EndSection

Section "Screen"
	Identifier    "Default Screen"
	Monitor        "Configured Monitor"
	Device        "Configured Video Device"
	DefaultDepth     24
	SubSection "Display"
		Modes "1280x800" "1024x768"
		Virtual	2704 1050
	EndSubSection
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "stylus"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "eraser"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
	Option        "Type"          "cursor"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "pad"
	Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
	Option        "Type"          "pad"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "touch"
	Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
	Option        "Type"          "touch"
	Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
	Option "BottomX" "915"
	Option "BottomY" "940"
	Option "TopX" "48"
	Option "TopY" "90"
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice   "stylus"  "SendCoreEvents"
	InputDevice   "eraser"  "SendCoreEvents"
	InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
	InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
	InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this typeEndSection
EndSection

Section "Device"
	Identifier    "Configured Video Device"
	Driver        "intel"
	Option        "monitor-HDMI-1" "HDMI-1"
	Option        "monitor-HDMI-2" "HDMI-2"
EndSection

---

### Post by boutch55555 on 2009-04-21
try

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/ttyS0" # SERIAL ONLY
Option "Type" "stylus"
Option "Button1" "1"
Option "Button2" "3"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

---

### Post by Favux on 2009-04-21
Hi nimonika,

boutch55555 is right, although you probably don't need the [Option "Button1" "1"] line, since that should be default.

Does the X200t have "touch"?  Where your finger can replace the stylus on the screen?  I ask because you have coordinates for "touch" in that section.  If not then you can remove the "InputDevice" section for it and also remove it in "ServerLayout".  I assume your stylus has and eraser and one button.

The same applies to "cursor" which refers to a Wacom mouse for an external Wacom graphics tablet.  And also "pad" which refers to control buttons on the external Wacom graphics tablet.  Don't forget the "ServerLayout" entries for them.

To calibrate your tablet use "wacomcpl" described in section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I hope this was helpful.

---

### Post by nimonika on 2009-04-23
Thanks a lot. Yes my laptop does have touch. I shall make the changes and update the post if it works.

---

### Post by lhs2miler on 2009-04-23
Can you let me know if you have the new version of ubuntu 9.04 installed on the x200t, tablet?  I was thinking about making the transition but am afraid of the incompatibilities.
thanks,
lhs2miler:)

---

### Post by nimonika on 2009-05-01
The right click setting worked. Thanks. I am not yet upgrading to Jaunty.

---

### Post by vfrjim on 2010-12-01
Sorry to dig up an old thread but I just took the leap to Ubuntu 10.04 and I am having the same problem as the OP had but I cannot find the xorg.conf file to edit like the one he showed here, mine does not look the same at all:

> Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Can someone help?

Thanks

---

### Post by Favux on 2010-12-01
Hi vfrjim,

Welcome to Ubunut forums!

You have an X200t?

You could use the xorg.conf but it is preferred you use the 10-wacom.conf in xorg.conf.d that you found.  You can just add it to the serial snippet.  There's a second serial snippet available too, let's first find out which one you need by looking at the output of:
```
xinput --list
```
in a terminal.

You can also do it through a xsetwacom script you've enabled to autostart.  Does your stylus have 1 or two buttons?  An eraser?  Touch or multitouch?

---

### Post by vfrjim on 2010-12-01
> **Favux said:**
> Hi vfrjim,

Welcome to Ubunut forums!

You have an X200t?

You could use the xorg.conf but it is preferred you use the 10-wacom.conf in xorg.conf.d that you found.  You can just add it to the serial snippet.  There's a second serial snippet available too, let's first find out which one you need by looking at the output of:
```
xinput --list
```
in a terminal.

You can also do it through a xsetwacom script you've enabled to autostart.  Does your stylus have 1 or two buttons?  An eraser?  Touch or multitouch?


I do not think it is a multi-touch, the stylus has 1 button and a eraser.

Here is the output from the xinput command:

> jim@jim-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (17ef:480c)                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]
jim@jim-laptop:~$ 


---

### Post by Favux on 2010-12-01
OK, with the default 10-wacom.conf in Lucid and the default 0.10.5 xf86-input-wacom it should look something like:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Button2" "3"
EndSection
```
If you want to add it in xorg.conf.d.

So you have touch?  As I mentioned you can also configure through a xsetwacom script.

---

### Post by vfrjim on 2010-12-01
> **Favux said:**
> OK, with the default 10-wacom.conf in Lucid and the default 0.10.5 xf86-input-wacom it should look something like:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Button2" "3"
EndSection
```
If you want to add it in xorg.conf.d.

So you have touch?  As I mentioned you can also configure through a xsetwacom script.

I have touch but after I added this to the file, it requires me to press the side button on the stylus to use the right-click option, normally I just press it against the screen to make the right-click show up, any idea on how to do this?

How is a script done?  I am a windows user for years.  Also, any adjustments on sensitivity other then the mouse options?

Thanks!

---

### Post by Favux on 2010-12-01
Hi vfrjim,

> after I added this to the file, it requires me to press the side button on the stylus to use the right-click option, normally I just press it against the screen to make the right-click show up, any idea on how to do this?
That's normal behavior.  The stylus tip is by default left click.  So I'm no sure what you are asking.  Are you saying you want to just press the button to right click and not touch the stylus tip also?  That would be hover mode (TPCButton "off").

Here's the script.  As you can see there are plenty of sensitivity adjustments you can make.  I just converted my usb tablet pc script to work with your serial tablet.  Barring a few defaults (like RawSample) being different it should work fine.  I did comment out the coordinates because yours are likely to be different.  But you can see how to add them.  To explore options use 'man xsetwacom' in a terminal and it will tell you how to get parameter of a device for example.

The original script is from post #2 on the [Bamboo P&T HOW]("http://ubuntuforums.org/showthread.php?t=1515562") TO thread.  Instructions for installing the script are in IV. in the HOW TO.

---

### Post by vfrjim on 2010-12-01
What normally happens when you press the stylus against the screen for an extra second or so that it triggers a right click automatically.  I know that I can do this in the Accessibility options in the mouse settings, but it is more sensitive in windows 7 then I can configure in that setting.  I will check out the script too see how else I can set it. I do appreciate all the help.

Jim

---

### Post by Favux on 2010-12-01
Hi Jim,

I gottcha now.  As far as I know simulating a right click by holding the stylus tip down has to be done through the mouse Accessibility option.

---

