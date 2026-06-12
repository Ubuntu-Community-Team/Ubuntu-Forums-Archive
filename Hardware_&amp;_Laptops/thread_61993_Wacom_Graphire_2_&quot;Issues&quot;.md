---
title: "Wacom Graphire 2 &quot;Issues&quot;"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by red_two on 2005-09-02
I'm only 3 days into the process of finessing my Ubuntu distro, and everything's gone pretty well...with a few exceptions. The most pressing of these is the behavior of my Wacom Graphire 2 tablet/mouse.

I use the tablet mouse in lieu of a ps/2, and I much prefer it to an optical mouse. 5.04 hotplugged the device correctly, and in my GNOME device manager, all the peripheral data seem correct.

The mouse movement is smooth, and the left-click and right-click functions work fine. But the mouse wheel seems to be inverted. Scrolling up makes pages scroll down, and vice versa. Also, and more irritating to me, whenever you lift the mouse off the pad to reposition, the cursor swings off and drops back where you reposition it.

Writing that last part out doesn't make as much sense as it should, but as anyone who's dealt with a tablet mouse will know, this shouldn't happen. When you lift the mouse off the pad, the cursor should remain where it is, and pick up where it left off when you reposition it.

(Still sounds confusing, I guess)

In any case, I've seen about a half dozen tutorials on these forums and on the wacomlinux site. But they all seem to be in response to out-of-date or incorrect drivers. Everything looks correct on mine. I've updated the 2 Wacom packets present in Synaptic, and that still didn't correct the issues.

From the number of posts regarding Wacom issues, I know there are other Ubuntu users who've dealt with tweaking their tablets. If any of you can help me out, I'd be really grateful!

Thanks!

---

### Post by Ventajou on 2005-09-05
Hi,

I just came across the problem myself and here's how to easily fix it:
Open xorg.conf (sudo gedit /etc/X11/xorg.conf) and look for "ZAxisMapping" option in the "InputDevice" section. Change the value from "4 5" to "5 4" and you're set!
Now you can just restart the X server by pressing Ctrl+Alt+Backspace.

---

### Post by cosimo on 2005-11-19
Hello all,
 I have different problem with wacom scroll wheel.
 i installed the driver and even have pressure sensitivity in gimp, however now there are two problems.
 First the scroll wheel doesn' work. When on a web page , if I try to scroll it just jitters the page.
Second , in Gimp, if I draw a line with the stylus and then try to change brush, or anything else, it stays on the brush and I cannot get out of it. Everything is "dead" to the stylus except the brush I was using. I have to continually click off the page, many times to get that brush off the stylus pointer. Here is my xorg file;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "cursor"
        Option "USB" "on"
        Option "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "stylus"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection

---

### Post by cosimo on 2005-11-22
Hello all,
 Well I have solved most of the problems with the graphire tablet from wacom, however one problem has arisen .
 I have pressure sensitivity in Gimp. That works fine but, if, for example, I choose the brush, then brush a few strokes with pressure, yeah, then try to get another tool,
 it will not release the brush from the pointer and I cannot get to anything.
 any suggestions?
 thanks
 Coz

---

### Post by 23meg on 2005-11-22
[QUOTE=cosimo]Hello all,
 Well I have solved most of the problems with the graphire tablet from wacom, however one problem has arisen .
 I have pressure sensitivity in Gimp. That works fine but, if, for example, I choose the brush, then brush a few strokes with pressure, yeah, then try to get another tool,
 it will not release the brush from the pointer and I cannot get to anything.
 any suggestions?
 thanks
 Coz[/QUOTE]
Can you list the options you've set for your tablet devices in GIMP's Input Devices configuration?

---

### Post by Curtisc on 2005-11-22
I've got the same problems as both of you.  I've followed all the HOWTO's and everything and tried all sorts of things, with results varying from "almost" working to losing my GUI entirely.  The best I ever got had the following issues:

1. Mouse repositioning itself when I lift it off the tablet and put it back down
2. Jittering of the page instead of scrolling
3. "Stuck" in whatever pen mode I'm in in GIMP until I click spastically
4. No difference between eraser and pen in GIMP

I didn't edit the input device settings in GIMP at all, I just left them as default.  Also, when I first installed Ubuntu without doing anything, I had the inverted scroll-wheel problem, the mouse was working in "absolute" mode, and there was no pressure sensitivity or difference between pen and eraser.

---

### Post by cosimo on 2005-11-23
hello,
 thanks for the reply I didn't think anyone would answer so forgive me for the late reply .
 First I solved the jitter problem by adding another ZAxisMapping to the xorg file;

Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "cursor"
        Option "USB" "on"
        Option "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "stylus"
        Option "USB" "on"
        Option "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection
 The settings in gimp are as follows;
 Eraser set to screen x-1, y-2, xtilt-4, ytilt-5
stylus set identical to eraser
Cursor is disabled but I did that after the problem arose thinking it might help
 But I also noticed after having installed MoHo that the tip of the stylus doesn't work at all and I can only draw with the eraser side of the sylus.
Go figure. i am suure that the second problem is because of MoHo and not just the settings. although whoknows?
thanks
coz

---

### Post by 23meg on 2005-11-23
[QUOTE=Curtisc]
I didn't edit the input device settings in GIMP at all, I just left them as default.  [/QUOTE]
You should set all your tablet devices to screen mode in extended input devices setup.

---

### Post by cosimo on 2005-11-23
Hello,
 I wanted to add that when I go into gimp and the brush tool is not released I can force the release by hitting alt+r. That brings up the filters menu and releases the cursor
 Thanks
 Coz

---

### Post by 23meg on 2005-11-23
What exactly is MoHo?

---

### Post by cosimo on 2005-11-23
Hello again, for the guy having problems with the driver being out of date , you need to go to wacom's site and download the driver from the link that they give for the most recent driver.  it made all the difference. I have to say that the wcom mouse works better than any optical I have after putting in the suggested wacom driver
 sorry for the repeated entries
 Coz

---

### Post by Curtisc on 2005-11-23
Sorry, when I said I left the gimp settings as default, I meant all the numbers stuff (x -1 y-2 etc).  I tried both screen and window for my stylus and eraser.  Leaving it on screen (Which is what I prefer) I'm still getting "stuck" in the paintbrush mode.  Using alt-r to bring up the filters, I can get out of the paintbrush, but if I try and go back to drawing again, I can't.  If I switch tools, let's say to the eraser, I get the little "eraser" icon next to my cursor, but I don't get the drawing circle to appear.  So basically, I can use one tool at a time, and then I have to alt-r, save my stuff, restart gimp, and choose a different tool.  Not the most efficient.  I *think* my driver is up to date - is there a command to find out what version I'm running?

-cosimo: when you say the mouse works great, do you still get the cursor relocating when you pick up the mouse and put it back down, or is that fixed?

---

### Post by cosimo on 2005-11-24
hello,
well MoHo is a 2d animation software for just about any OS.
It is not a free application though.
here is the url : [http://www.lostmarble.com/](http://www.lostmarble.com/)

---

### Post by cosimo on 2005-11-24
Hello .
My mouse cursor snaps to position of the mouse like the stylus cursor

---

### Post by Curtisc on 2005-11-25
Working!

My tablet now behaves as it does in windows with one exception - I have to choose the value for the eraser when I start gimp, it defaults to paintbrush and not eraser.  Otherwise, pressure sensitivity, difference between stylus and eraser, correct scrolling of the mouse, and the cursor does not snap to the position of the mouse like the stylus.

I decided to go back and check to see that I had it on the right event... I did, and cat event2 produced garbage from the tablet - but there was also a new device called "wacom".  That produced garbage too, so I changed my xorg.conf to that, and voila.  Here's the relevant portions of my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "cursor"
  Option        "USB"           "on"
  Option	"ZAxisMapping"	"4 5"
  Option	"Speed"		"2"

EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice    "cursor"    "SendCoreEvents"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
EndSection
```

Hope this helps!

---

### Post by cosimo on 2005-11-26
Hell all,
 I tried changing everything to wacom in the xorg but no difference. i still have the problem of the cursor not releasing the tool untill I press Alt+r in GImp.
 I have the snap to stylus, pressure sensitivity, etc, but this issue of it not releasing the tool is intolerable. Gimp works great on windows, as does the wacom driver, but I am not convinced that this is the way to go for anyone who is into graphics, on any level, pleasure or professional. if this issue cannot be solved, then Ubuntu will remain a obscure Os for the home user, who uses only a mouse to access the internet and email.
 That's a shame. i have been trying to convince clients to switch to Ubuntu, however, I have been careful to pick only thoses clients who do only what i said, email , internet, and  such.
  i will keep checking back to see if any of you have come up with a solution to this.
 Thanks all for listeneing .
 Coz

---

### Post by Curtisc on 2005-11-28
I had to reinstall ubuntu recently (Deleted something that was apparently important), so I went through all the steps to get the wacom up and running again and it pretty much works.  For some reason, I didn't get the "wacom" event to appear until I rebooted, but once it did it's now working.

The only problem I have is that if I want to switch from pen to eraser, I need to be hovering over the canvas.  If I'm over the tool bar or the desktop or anywhere else, the eraser doesn't seem to cause any response.  Other than that, it works fine, no problems with releasing tools or anything.  I read so many stories of varying degrees of success with tablets; does anyone have a completely functioning tablet?  My issue is fairly minor compared with not releasing tools, but it would be nice for it to be perfect.

---

### Post by cosimo on 2005-12-20
Hello all
Well I believe I have solved the wacom problems for the most part.
 The first problem is installing the linux wacom driver, Big mistake!
In ubuntu all that is necessary is "wacom-tools" and "wacom-kernel-source", both, as you probably know, avaiable from synaptic. 
   Everything is working, including the release of the tools icon in gimp, i just have to click the switch on the stylus to release it.
Not perfect but damn close.
  The cursor snaps to both the stylus and the mouse system-wide.
I have had no major problems since the exclusion of the linus wacom driver.
 My xorg.conf file was , all along, correct.
 Thanks to all that tried to help.
 I can be a doof at times.
 coz

---

### Post by CyBuzz on 2007-03-03
I cant seem to find the drivers on the wacom site.

I have my mouse working, though there are issues.  Looks like the pen works fine in Gimp, Inkscape and Krita
1.  Scroll is inverted
2.  the buttons on the sides of the mouse dont work.
3.  On the login screen, I need to touch the pen to the pad before the mouse will work.

I have wacom-tools, wacom-kernel-source and xserver-xorg-input-wacom installed.

Here is my xorg.conf
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
	FontPath	"/usr/share/fonts/X11/misc"
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/wacom"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option	"USB"		"on"
#  Option        "ForceDevice"   "ISDV4"           
  Option 	"PressCurve"	"50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option	"USB"		"on"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option	"Mode"		"relative"
  Option	"USB"		"on"
  Option	"ZAxisMapping"	"4 5"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
#  Option        "ButtonsOnly" "on"
#  Option        "Button9" "2"
#  Option        "Button13" "3"
  Option        "Device" "/dev/input/wacom"
  Option        "USB" "on"
  Option        "Type" "pad"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
#	InputDevice    "pad"       "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

