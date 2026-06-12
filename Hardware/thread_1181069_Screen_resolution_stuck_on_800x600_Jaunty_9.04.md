---
title: "Screen resolution stuck on 800x600 Jaunty 9.04"
date: 2009-06-07
forum: Hardware
---

### Post by LyonTamer on 2009-06-07
Hi. I thought I already posted this problem but cannot find it now, please forgive if I'm repeating. :)

I have a clean install of 9.04 on a Dell Inspiron 8000. I had previously upgraded in steps from 7.10 to 9.04 and then when I got the disk in the mail, I ran the clean install.

My monitor is capable of 1024x768 and it ran at that setting with the upgrade, but the clean install of 9.04 only offers two options, the 800x600 or 640x480. It shows my monitor as "unknown". I looked for a restricted driver for the monitor and no restricted drivers at all for this computer are listed, so I am unable to click on it to turn it on.

Help? Everything's ginormous on the screen, it's annoying.

---

### Post by sae.area on 2009-07-04
Hi,

after hours :-k of falling into every trap this system has to offer I've succeeded in changing the resolution from 800x600 to 1024x768.
Here is my story.

I have an E-Series laptop from Fujitsu-Siemems (Pentium III 800 Mhz, ATI Technologies Inc Rage Mobility M4 AGP) and installed Ubuntu 9.04 the wubi way (didn't want to start the repartitioning action). I had done it without burning the CD, just using MagicDisk (virtual CD/DVD drive) - saves me from going out and buying writable disks.

Installation is finished, resolution only 800x600.
Through some other erroneous behavior I figured that the installation wasn't complete and that it might have had something to do with doing the installation from the virtual CD. Maybe it would have been complete if I had a real CD in the real drive - didn't try it again.

After searching the net I've found that there is this command which should help:
> sudo dpkg-reconfigure xserver-xorg
All it let me do is set the keyboard settings, never asked for any graphic details. But looking at the other existing xserver-xorg modules, I noticed ati and r128. I tried the above command again this time with ati and later with r128. Both times a message came up that it couldn't find the files. Ok. Looking at the synaptics package management tool, I saw all those modules as being installed. I've reinstalled first just ati and r128, but with no success. So I reinstalled anything that said xserver.
Again no luck - dpkg-reconfigure stopped the error message of not finding the files, but it also wouldn't let me configure anything.

Back to the net and searching. I came across this guy having the same issue with Debian Lenny who had posted some great hints ([http://forums.debian.net/viewtopic.php?f=6&t=33620]("http://forums.debian.net/viewtopic.php?f=6&t=33620").
I found out that I had to use > Xorg -configure (this is of course in secure terminal mode - so no graphics). This will write a new xorg.conf file with lots of details - much different from the original. Copy the file over the old xorg.conf in /etc/X11/. But that didn't help. The xorg.conf file showed the card correctly and used ati as driver now, but it missed resolution settings and some other details.

On another page on the net I've found the following details:
> DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection


My xorg.conf file included lots of "Display" SubSections, but none included "modes" parameters and it was missing the "DefaultDepth" in the "Screen" section. I got rid of all "Display" SubSections except the one with Depth 24. Inserted the DefaultDepth line into the "Screen" section and Modes line into the one "Display" SubSection (adding 800x600, just for completeness). 
Then I read somewhere that I needed the following information: HorizSync and VertRefresh
And found something on the same page that looked like it would fit the screen of my laptop.  
> VertRefresh 60
HorizSync 31.5-90

I saved the file and restarted the machine. The login screen was already sharper, but when I logged in, the resolution was again, only 800x600. But this time the Display Control, offered 1024x768. Selected it and it worked.

Here is my complete xorg.conf file (but I recommend to run the > Xorg -configure command for your machine):
------------------------------------------------------------------
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "dri2"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	VertRefresh 60
	HorizSync 31.5-90
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "r128"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage Mobility M4 AGP"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
--------------------------------------------------------------------

I hope this helps.

Cheers!

UPDATE:

Use for DefaultDepth 16, instead of 24 and copy and paste the "Display" subsection with Depth 16. I just found a graphics error from an app disappearing after using 16.

---

