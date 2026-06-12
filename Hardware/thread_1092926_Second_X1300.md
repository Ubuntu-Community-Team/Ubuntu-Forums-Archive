---
title: "Second X1300"
date: 2009-03-10
forum: Hardware
---

### Post by linuxuser21 on 2009-03-10
I have a ATI X1300 and I really enjoy it.  I am thinking about getting a second one to add two more screens.  Would this be possible?
NOTE: I have EnvyNG installed for dual monitors.

---

### Post by linuxuser21 on 2009-03-11
Bump!

---

### Post by linuxuser21 on 2009-03-11
Bump.

---

### Post by Neo_The_User on 2009-03-11
Envy is terrible!

Here go to this thread and check the installation method I provided here and see if this helps.

[http://ubuntuforums.org/showthread.php?t=1091804&page=2](http://ubuntuforums.org/showthread.php?t=1091804&page=2)

Also, for only 2 GPUs try this out:

sudo aticonfig help or --help or man aticonfig. There is a command for the usual crossfire support somewhere in there. ;)

---

### Post by linuxuser21 on 2009-03-11
Thank you so much for that information.  I just very desperate to find a solution for dual monitors and Envy worked.  I haven't had any problems with it so far.  What makes it so terrible?

---

### Post by Neo_The_User on 2009-03-11
[http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=2)

I always had a bad experience with Envy. Its highly unsupported. Nobody uses it.

---

### Post by linuxuser21 on 2009-03-11
Do you suggest I uninstall Envy and do something else to enable dual monitors?

---

### Post by Neo_The_User on 2009-03-11
Yes I do. Are you familiar with Xrandr? You can also use the Catalyst control panel when using fglrx.

---

### Post by linuxuser21 on 2009-03-11
No, what is Xrandr?

---

### Post by linuxuser21 on 2009-03-11
The Catalyst Control Center just resets every time I startup my computer.

---

### Post by Neo_The_User on 2009-03-11
xrandr is a helpful command line tool for configuring xorg.conf. Before you do anything though, I strongly recommend you remove the ATi drivers using envy.

---

### Post by linuxuser21 on 2009-03-11
How do I find out about Xrandr?

---

### Post by linuxuser21 on 2009-03-11
What's the command line for uninstalling Envy?

---

### Post by Neo_The_User on 2009-03-11
well unless you plan on using the open source drivers, you might not want to use xrandr and you would rather just do it all through fglrx catalyst.

Terminal:

```

man xrandr

```

Lots of documentation about it.

Do not uninstall Envy itself. You want to uninstall the Ati drivers first using Envy. then you can remove envy.

---

### Post by linuxuser21 on 2009-03-11
I'm okay with open source drivers, just as long as it works.  Please bare with me, this is a big step for me.  lol.

---

### Post by Neo_The_User on 2009-03-11
well in xorg.conf you can edit it by hand as root via gksudo gedit or sudo nano and put in a virtual line under subsection display.

it would look a bit like this:

```

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
	Load  "glx"
	Load  "dbe"
	Load  "extmod"
	Load  "dri"
	Load  "xtrap"
	Load  "record"
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
	#DisplaySize	  410   260	# mm
	Identifier   "Monitor0"
	VendorName   "WDE"
	ModelName    "LCM-19w4"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
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
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R350 [Radeon 9800 Pro]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 2880 900	
	EndSubSection
EndSection

```

Last 3 lines is all really

---

### Post by linuxuser21 on 2009-03-11
I've done this at one time; however, I cannot remember how to view the xorg file.  How do I do it?

---

### Post by Neo_The_User on 2009-03-11
what editor do you like better? nano or gedit?

---

### Post by linuxuser21 on 2009-03-11
I've used Gedit in the past, but not nano.  Which one do you think would be best for me?

---

### Post by Neo_The_User on 2009-03-11
eh gedit will work fine. You sure you want to use the open source drivers? I'm not too sure it will work. Fglrx would most likely work over the open source drivers.

---

### Post by linuxuser21 on 2009-03-11
Does Envy replace the Fglrx drivers?  I used the Fglrx drivers before Installed Envy.  That was also when the Catalyst Control Center would just reset itself everytime I turned on my computer.

---

### Post by Neo_The_User on 2009-03-11
Envy doesn't exactly replace the fglrx drivers. Just use the ones from the ati website.

Terminal:
```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run

```

then follow the guide in the other thread. Good luck.

---

### Post by linuxuser21 on 2009-03-11
Thank you for all your help!  Hope I do this right.  lol.

---

### Post by Neo_The_User on 2009-03-11
fresh install. envy puts junk in the kernel that you can't pull out.

---

### Post by linuxuser21 on 2009-03-11
I did "sudo apt-get remove envy" and it said that it wasn't installed.  It must have gave me an error when I was installing it that I missed.  The fglrx drivers must have been doing it this whole time.  I'm going to try the stuff in the thread you told me to do.

---

### Post by Neo_The_User on 2009-03-11
mkay

---

### Post by linuxuser21 on 2009-03-11
It's installing right now.  So, what exactly is this going to do?

---

### Post by linuxuser21 on 2009-03-11
I just got a message saying "After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?"
I typed "y"
Then I got "Abort."
Is this a problem?

---

### Post by Neo_The_User on 2009-03-11
yeah. look ill be installing freebsd for next while so try and diagnose without my help for a bit

---

### Post by linuxuser21 on 2009-03-11
I just completed everything & my graphics seem to be running a lot more smooth.  It's nice.

---

### Post by Neo_The_User on 2009-03-12
Oh goodie! You're using the drivers from ATi?

---

### Post by linuxuser21 on 2009-03-14
> **Neo_The_User said:**
> Oh goodie! You're using the drivers from ATi?

Oh yeah!  It looks and preforms great too.  Had a bit of a scare though... I decided to do a bit of an experiment and put an nVIDIA card in my AGP slot to see what would happen.  I activated the necessary drivers and didn't catch that it disabled my ATi drivers.  When I restarted, I had no GUI and nothing at all on my screen attached to my nVIDIA card.  I freaked out and took the nVIDIA card out and restarted it.  After I enabled the ATi drivers again and everything was normal again.

---

### Post by Neo_The_User on 2009-03-21
heh. glad it came back. XD

---

### Post by linuxuser21 on 2009-03-22
Thank you for all your help with this.

---

