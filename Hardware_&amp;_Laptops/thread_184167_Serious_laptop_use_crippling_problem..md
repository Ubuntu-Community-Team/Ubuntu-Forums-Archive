---
title: "Serious laptop use crippling problem."
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by darkshadow on 2006-05-29
Up to yesterday I had it working perfect but something happened yesterday to revert to default settings

My problem is tap-to-click on my synaptics touchpad. I had it disabled by adding
Option "SHMConfig" "on"
Option "MaxTapTime" "0"
to my xorg.conf that worked fine for as long as I had it set but now tap-to-click is back and seriously causing problems for me. I can't even type as my thumbs keep resting on the pad and it counts as a click which moves where I am typing. I am unable to move the mouse without it thinking I started with a click or that I am holding the mouse down.

This is very serious for me as I have screwed up filesystems will in filemanagers just by accidently dragging folders and ending up with them moving into another.

---

### Post by tya on 2006-05-29
I'm sorry for a stupid question, but I don't understand your problem. "Worked fine for as long as I had it set", you say. So why don't you set it again? I suppose that a xorg update installed a new xorg.conf so you have to make the modification again?

---

### Post by darkshadow on 2006-05-29
Bad wording on my part. My xorg.conf was not changed those entries are still there.

---

### Post by darkshadow on 2006-05-30
Please anyone have any ideas I am getting extremely annoyed at my touch pad

---

### Post by tigrux on 2006-05-30
Install gsynaptics [1] and configure your touchpad properly. I had a vey similar problem and by using gsynaptics everything was solved.

[1] [http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by joshrobinson on 2006-05-30
omg mines been doing the same thing!! for the first like half hour everything is fine, no tap click no tap move nothing.. then all of a sudden out of nowhere the mouse pad gets a mind of its own and starts clicking, pasting, closing, and draging objects all over the place.. its a pain in the butt.. some update got us on that one

i will try that gsynaptics program

---

### Post by joshrobinson on 2006-05-30
just compiled and installed gsynaptic.. will report back later on if it fixed the problem.. the problem ususally takes awhile to start happening

---

### Post by darkshadow on 2006-05-30
I was going to try gsynaptics but since I would have to compile it and that would require a massive amount of dev files for other programs I just found qsynaptics in the repositories and it worked fine.
Thanks I would not of thought to look for a gui without your suggestion

---

### Post by tsb on 2006-05-30
Why not disable the touchpad while typing?  I'm still trying to figure out how you touch the pad while typing anyway.  Is your pad off-center?

---

### Post by joshrobinson on 2006-05-30
even with gsynaptics with touch disabled it still tap clicks when i dont want it to :-(

---

### Post by joshrobinson on 2006-05-30
bump.. anyone else having these problems with a laptop? i cant use the touchpad without it screwing everything up

---

### Post by slavik on 2006-05-30
no, but my Compaq V2000Z has a button to disable the mousepad completely ... I use it when I have an external mouse :)

---

### Post by joshrobinson on 2006-05-30
[QUOTE=slavik]no, but my Compaq V2000Z has a button to disable the mousepad completely ... I use it when I have an external mouse :)[/QUOTE]

yeah im using an external mouse right now.. the touchpad just screws everything up and pastes and moves stuff everywhere..highlights everything on webpages when i try to move the mouse.. it sucks

---

### Post by tsb on 2006-05-30
You could try to blacklist it perhaps.

---

### Post by Angafirith on 2006-05-30
I had a similar problem a while back, but I finally figured out how to fix it. The problems began when I upgraded to a newer kernel, which had changed the path of my synaptics touchpad device. When my old xorg.conf file still had the old path, it failed to recognize the touchpad and assumed that it was a normal mouse.

Look in your xorg.conf file, at the Synaptics Touchpad Section. In my file, it shows as such:
```
	Option		"Device"		"/dev/psaux"
```

If it is different from this, you may want to try changing it to this and restarting X.

---

### Post by joshrobinson on 2006-05-31
[QUOTE=Angafirith]I had a similar problem a while back, but I finally figured out how to fix it. The problems began when I upgraded to a newer kernel, which had changed the path of my synaptics touchpad device. When my old xorg.conf file still had the old path, it failed to recognize the touchpad and assumed that it was a normal mouse.

Look in your xorg.conf file, at the Synaptics Touchpad Section. In my file, it shows as such:
```
	Option		"Device"		"/dev/psaux"
```

If it is different from this, you may want to try changing it to this and restarting X.[/QUOTE]

its in there as psaux just like yours :-(

---

### Post by HankB on 2006-06-01
I have synaptics touch pad on an HP Limited Edition L2000 (AMD64-Turion) and I am also experiencing problems with the touch pad. I used to really have a problem with the cursor jumping around until I used qsynaptics (with breezy) to disable the touchpad following key strokes. That no longer works:


[edit] I had disabled SHMconfig in xorg.conf and added it back with

  Option        "SHMConfig"     "on"

I can now run qsynaptics and synclient and change settings, but I haven't solved the problem.

[/edit]

In addition, the touch cursor really wants to drag whenever I move it, causing me to select text in windows, drag stuff across my desktop etc.

The version for the synaptics driver is "0.14.3+seriouslythistime-0ubuntu3" so it appears that there were problems getting it working and I have to add, seriouslynotyet. :(

Too bad. The upgrade was cake on my T30.

Hopefully they will get this resolved Real Soon!

-hank

---

### Post by HankB on 2006-06-02
I solved the problem by manually installing the latest synaptics driver. Apparently there are problems with 0.14.3 and AMD64. I downloaded the 0.14.4 driver from the site linked from [http://web.telia.com/~u89404340/touchpad/index.html](http://web.telia.com/~u89404340/touchpad/index.html) 

I also installed the xserver-xorg-dev package. Then I unpacked the driver and typed 'make' to build it. I renamed /usr/lib/xorg/modules/input/synaptics_drv.so and copied synaptics_drv.o (yes, that's .o replacing .so) to that directory. When I reloaded the driver the dragging behavior went away.

Unfortunately synclient and qsynaptics no longer work so I have the problems with the cursor jumping around the screen. :(

At least this is closer to usable.

---

### Post by edulinux on 2006-06-03
Hey guys, i was having the same problem with the nasty drag/select. It only happens to me on Ubuntu amd64, on i386 i have no problems (i have both OS  on the same laptop).

It seems to be a problem with the default driver, i found no way to fix it changing parameters.

Fortunatly, i found a really simple way to change a driver to a newer version:

[http://www.ubuntuforums.org/showpost.php?p=919342&postcount=8](http://www.ubuntuforums.org/showpost.php?p=919342&postcount=8)

In brief, what you need to do is...

```
sudo apt-get install xfree86-driver-synaptics
sudo ln -sf /usr/X11R6/lib/modules/input/synaptics_drv.o /usr/lib/xorg/modules/input/synaptics_drv.o
```

It will remove the ubuntu-desktop package and the synaptics driver that comes with xorg, but it's not a problem. qsynaptics keeps working after this update.

I must thank to thediviner. I hope it works for you too.

(My laptop is an HP pavilion zv5000)

---

### Post by HankB on 2006-06-03
Yes, Thanks! that installs the newer version of the synaptics driver and w/out working outside the package management system.

thanks,
hank

---

### Post by obi-nine on 2006-06-04
[QUOTE=HankB]Yes, Thanks! that installs the newer version of the synaptics driver and w/out working outside the package management system.
[/QUOTE]

That appears to only work with ubuntu. On kubuntu it removes the xorg. driver and kubuntu-desktop!

I don't think this is a solution for kubuntu users.

obi9

---

### Post by medy on 2006-06-05
I installed xfree86 synaptics driver and put it in xorg modules as you described, but it did not work.

My problem with touchpad is:
- way to quick
- clicking by itself
- it freezes for 15s or so
- cannot click on a newly open windows
* but after some time 20-30s it works again
 
my laptop is HP Pavilion dv5057EA with 32bit Desktop Dapper Ubuntu on it.

running qSnaptics gives me this (weird)
```
medy@mikozaver:~$ qsynaptics
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
users home is /home/medy
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
```

and my xorg looks like this:
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "si"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by HankB on 2006-06-05
The message 
```
Can't access shared memory area. SHMConfig disabled?
```

Means you need to add:
```
	Option	    "SHMConfig" "on"
```

to your xorg.conf in this section:
```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection
```

I don't know if that will solve the driver problems but it should get qsynaptics working.

---

### Post by medy on 2006-06-06
thank you, "SHMConfig" "on" worked and tocuhpad seems to behave normaly (at this momement:)

and have a middle button on my touchpad, yuhheeej! 

thx!

---

### Post by jonwatson on 2006-06-06
[QUOTE=joshrobinson]even with gsynaptics with touch disabled it still tap clicks when i dont want it to :-([/QUOTE]

I added 

[INDENT]"TapButton1" "0"
"TapButton2" "0"
"TapButton3" "0"[/INDENT]

to my xorg.conf in the Synaptics section, restarted X and it stopped the tap. I hate that feature.

---

### Post by Patsoe on 2006-06-06
Glad I saw this topic coming by... I thought I was doing something funny. It is a really weird bug, because at times the touchpad works fine, then suddenly it becomes all "sticky" in that every move counts as a drag.

I already had a problem where I completely unintentionally moved a line from a shell script that was somewhere on a webpage into a terminal - it started executing! Luckily it didn't run with the right permissions...

We should inform the developers ofcourse. Has anyone already started a bug report? Otherwise I could do so towards the weekend sometime.

---

### Post by HankB on 2006-06-06
[QUOTE=Patsoe]
We should inform the developers ofcourse. Has anyone already started a bug report? Otherwise I could do so towards the weekend sometime.[/QUOTE]

The problem has been fixed in the syaptics driver that was released in Nov 2005. Our problem is to get the most recent driver packaged with Ubuntu. It seems that the newer driver (0.14.4) is included, but not in the package that gets installed by default.

There are already two Ubuntu bug reports for this so I would not add more.

One is [https://launchpad.net/bugs/34392](https://launchpad.net/bugs/34392)

---

### Post by Patsoe on 2006-06-10
I didn't like the fact that installing the xfree86 package would remove the standard package. One point is, that you might expect that whenever the xorg package would receive an update this will be at least version 0.14.4 - so after an update there's no longer any point for us to use the xfree86 version.

Since the xfree86 version works fine, there's no need for the hassle of compiling the driver yourself. I finally  just got the package from [http://packages.ubuntu.com/dapper/x11/xfree86-driver-synaptics](http://packages.ubuntu.com/dapper/x11/xfree86-driver-synaptics) and extracted (using the Archive Manager) the three files synclient, syndaemon and synaptics_drv.so. I backed up the original files, which are in /usr/bin and in /usr/lib/xorg/modules/input, and then put the extracted files in their place (using sudo to get the ownership right).

This way nothing complains about dependencies :) plus, when an updated xorg version comes out you automatically start using that again.

---

### Post by m1l3s on 2006-06-10
There is another way to fix the weird touchpad issue as well.  I used tpconfig - it's a touchpad config app that you can read the man page for all the details, but essentially the command "sudo tpconfig --tapmode=0" solved the problem.  Ubuntu is thinking that you're tap clicking on everything and starts to wig out - disabling that feature brings it back to normal.  And oddly enough, when I want to tap on something, it still allows me to.  Who knows...

---

