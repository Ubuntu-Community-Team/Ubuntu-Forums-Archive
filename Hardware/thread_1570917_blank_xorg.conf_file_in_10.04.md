---
title: "blank xorg.conf file in 10.04"
date: 2010-09-08
forum: Hardware
---

### Post by Radissthor on 2010-09-08
Hello Everyone,

I'm trying to configure touchpad options in a Dell Inspiron 11z with a newly installed Lucid Lynx. I installed synaptics and gsynaptics but when I go to System-->Preferences-->touchpad, it says:
```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

And when I try to edit the xorg.conf file with

```
gksudo gedit /etc/X11/xorg.conf

```

I get a blank file... Any guesses? 

PS: Yes, I made sure I'm typing th capital X

---

### Post by wojox on 2010-09-08
What graphics card/chip do you have?

```
lspci | grep VGA
```

---

### Post by colorpurple21859 on 2010-09-08
X  doesn't need xorg.conf to run unless there are special needs. Run > sudo Xorg -configure to create a xorg.conf.

---

### Post by Radissthor on 2010-09-08
> **colorpurple21859 said:**
> X  doesn't need xorg.conf to run unless there are special needs. Run  to create a xorg.conf.

running that command gives:

```
natalia@Inspiron11z:~$ sudo Xorg -configure 

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

As for the lspci command, the output is:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

I once erased the hardrive with the rm command, so I don't want to mass anything up... any help?

---

### Post by colorpurple21859 on 2010-09-08
Sorry, fail to mention you have to do this with X shutdown 
> sudo init 1 will drop you to recovery mode where you can enter a root shell to create an xorg.conf file

---

### Post by Radissthor on 2010-09-08
> **colorpurple21859 said:**
> Sorry, fail to mention you have to do this with X shutdown 
 will drop you to recovery mode where you can enter a root shell to create an xorg.conf file

Uhhm, All that did was to send me back to a terminal-like screen where it got stuck. I had to reboot. 
Then tried again. The same screen. This time, there were more lines. The last one says:

init: avahi-daemon main process ended, respawning

But nothing... it's stuck and I have to turn off and on again...

---

### Post by wojox on 2010-09-08
Yeah you need to be in recovery mode to do this. Try [No xorg.conf found in /etc/X11 (Ubuntu 10.04)]("http://ubuntuforums.org/showpost.php?p=9431354&postcount=8")

---

### Post by colorpurple21859 on 2010-09-08
That worked on my system, However try>  sudo stop gdm then hit altctrlf1 to change to a console, log on and then run>  sudo Xorg -configure  the run > sudo start gdm

---

### Post by Radissthor on 2010-09-08
> **colorpurple21859 said:**
> That worked on my system, However try then hit altctrlf1 to change to a console, log on and then run  the run

That sent me again to a terminal-like screen where it says:
```

fsck from util-linux-ng 2.17.2
/dev/sda1:clean, 137358/18989056 files 1802827/75947265 blocks
usb_id[706]: unable to access 'devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input7/event7'

*starting AppArmor profiles
Skipping profile in /etc/apparmor./disable: usr .bin .firefox 

[OK]
*setting up sensors limit     [OK]
*speech-dispatcher configured for user sessions 
*Starting Common Unir Printing System: cupsd    [OK]
*PulseAudio configured for per-user sessions
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
```

I think it's worth noticing the 

unable to access 'devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input7/event7'


and the fact that the Speech-dispatcher and the PulseAudio options are not [OK], and are actually marked with a red star

Anyways... that's when it gets stuck... I think something weird is happening...

---

### Post by colorpurple21859 on 2010-09-08
then try it this way hit altctrlf1, login, sudo stop gdm. sudo Xorg -configure. sudo start gdm.

---

### Post by Radissthor on 2010-09-08
> **wojox said:**
> Yeah you need to be in recovery mode to do this. Try [No xorg.conf found in /etc/X11 (Ubuntu 10.04)]("http://ubuntuforums.org/showpost.php?p=9431354&postcount=8")

Thanks... That link kindda worked.... I held shift on boot and enter recoverymode. Then, I went to root shell and typed the 

sudo Xorg -configure

and it worked... Then, it the thread it says I have to move the new xorg.conf file by running:

cd /root/xorg.conf.new /etc/X11/xorg.conf

Then it says:

just replace /root with whatever directory it happens to be in when it's created.

I don't get that last part. What am i supposed to replace /root by? The terminal says  I'm in root, I thing. The line to write in says
root@Inspiron11z:~#

Thanks!... I'm halfway there!

---

### Post by colorpurple21859 on 2010-09-08
what it is telling you do  is copy xorg.conf.new to /etc/X11/xorg.conf> cd /root/xorg.conf.new /etc/X11/xorg.confshould be > sudo cp /root/xorg.conf.new /etc/X11/xorg.conf xorg.conf.new may be in your home directory which it should be this  > sudo cp ~/xorg.conf.new /etc/X11/xorg.conf or   > sudo cp /home/?/xorg.conf.new /etc/X11/xorg.conf if your already root then don't need sudo at the beginning

---

### Post by Radissthor on 2010-09-08
Awesome... the xorg.conf file is there!! thanks a lot guys!!! I'll mark the thread as Solved...

One last thing... Regarding my original obective, which is to run gsynaptics, the message I posted in the first post:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

But I can't find any part where it says SHMConfig...This is my xorg.conf file:

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
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
	Load  "dri"
	Load  "extmod"
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
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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
	EndSubSection
EndSection

```

---

