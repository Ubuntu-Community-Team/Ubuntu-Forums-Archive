---
title: "[SOLVED] Problem: Sony Vaio VGN-250 &amp;amp; external projector via i855crt"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by wieman01 on 2006-07-24
Hello Folks, 

I have been trying to teach my laptop to connect to an external device (Sony projector) via the normal video output but so far I have not been successful. 

I gave i855crt and i810switch a shot only to discover that it produces a blurred, almost white screen when connecting it to an external device (like an LCD display or projector).

I played around with all kinds of settings, but to no avail. Having seen other posts concerning this problem on the web, I wanted to reopen this and ask if anybody knows a solution to this one.

Cheers, guys! This is a tough one!

---

### Post by wieman01 on 2006-07-24
Anyone? Apologies for bumping this up...

---

### Post by shaviro on 2006-07-29
This is just to say that I am having precisely the same problem with my Sony Vaio PCG-TR5AP laptop. I am a teacher, and I really need video out to show presentations to my classes. But nothing I have been able to do gets rid of the bleached-out projected image...

---

### Post by wieman01 on 2006-07-29
> **shaviro said:**
> This is just to say that I am having precisely the same problem with my Sony Vaio PCG-TR5AP laptop. I am a teacher, and I really need video out to show presentations to my classes. But nothing I have been able to do gets rid of the bleached-out projected image...

Ok, this makes two of us then. Glad to hear I am not on my own although I know it must be a pain for you.

I'll keep searching and keep you posted. Perhaps I'll find something in the weeks to come.

Anybody?

---

### Post by wieman01 on 2006-09-09
Again answering my own question... This is the right file which works for me. Now enjoying movies on my external projector. :-)
[HTML]Section "Device"
	Identifier	"Internal Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"	"CRT,LFP"
	Screen 		0
EndSection

Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite" 
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	HorizSync	30-60
	VertRefresh	50-75
	Option		"DPMS"
	Modeline    	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection	
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Head"
	Screen		"Internal Screen"
	Screen		"External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option  "Composite" "Enable"
#EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection
[/HTML]

I had to add this line: 
> Option		"MonitorLayout" "CRT,LFP"
Plus the "DefaultDepth" of both screens must be the same.

If I want to turn it off, I simply comment out this line & restart the x-server:
> #Screen		"External Screen" RightOf "Internal Screen"

---

### Post by wieman01 on 2006-09-18
Sound like Xinerama is what you're looking for. As said you cannot activate it by a click of a button, but anothoer guys & I had a similar question and could resolve it this way:

[http://www.ubuntuforums.org/showthread.php?t=237640]("http://www.ubuntuforums.org/showthread.php?t=237640")

---

### Post by Peacepunk on 2006-09-22
Sony vgn-t17gp (thailand) with 1280x760 screen, patched with 955resolution for widescreen & i810switch for VGAreplicator:

laptop screen perfect (dapper and breezy), blurry external output on excellent old 15" Trinitron CRT 1024x768.

I looked @ the 2 recommended posts, and can't figure out if we face the same issue with the same kind of stuff.

Have you guys:
1) 100% solved the issue ?
2) have a widescreen laptop wired to not-widescreen device ?
3) have a laptop that is NOT twinheads, means VGA-output being only a replicator ?

I am abit afraid of fooling around with xOrg.conf, and do not undersand how it defines what's "in" the laptop & what's "out" in terms of screens.

I believe Xinerama not to apply for me, as I do not have a dual-head laptop.

thanks

jPhilippe

---

### Post by wieman01 on 2006-09-22
Cambodia... great! Nice to meet you, mate!

As for you questions:

1) 100% solved.
2) My projector & external LCD display are both non-widescreen.
3) I am using the VGA-output.

Don't worry about messing around with you xorg.con, make a safety copy of it before we go ahead. We are here to help you with the rest & recovery should anything go wrong.

Still want to try? I can take the challenge. :-)

---

### Post by Peacepunk on 2006-09-24
> **wieman01 said:**
> Cambodia... great! Nice to meet you, mate!

Still want to try? I can take the challenge. :-)

Yeah, sure: These two last days without internet... Great to keep a topic alive on a forum ! Nevertheless, Hello HK !

About "3": is your laptop external output a replicator or a real second screen plug ? I cannot, in my original XP/VAIO have different things on the two screens - Replicator only.

i810switch does plug something to the CRT that is sharp on the left, and progressively blurred 'till unreadable on the right + how'd you call that in English ?, horizontal lines crossing the screen & moving top to bottom - must be a word for that. Another than shitty, I mean.

I dunno where Xinerama sits, unknown to synaptic.

The CRT (Sony Trinitron 100gs) usually sits atop a P4 with SuSE93: this thing is older than I can remember, and still way better than anything I would buy here. Cost me USD400 at the time, well worth it.

I've been trully reading the links & still feel lost.
-Practical: section of my suse93 xorg.conf, for reference as I am satisfied with the settings:

> /etc/X11/xorg.conf /etc/X11/

Section "Monitor"
  Option       "CalcAlgorithm" "CheckDesktopGeometry"
  DisplaySize  285 215
  HorizSync    31-48
  Identifier   "Monitor[0]"
  ModelName    "1024X768@60HZ"
  Option       "DPMS"
  VendorName   "--> VESA"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1024x768" 65.00 1024 1048 1184 1344 768 771 777 806
EndSection

Section "Screen"
  DefaultDepth 16
  SubSection "Display"
    Depth      15
    Modes      "1024x768" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1024x768" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1024x768" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1024x768" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1024x768" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

My graphic device is an Intel 82852/855GM inetgrated, driver is i810.

> Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Tech Data of my screen:
```


Sony GS Series Model 100 15 inch CRT Monitor 
Key Features
Monitor Type	CRT
Size	15 inch
Max. Resolution	1280 x 1024
Min. Resolution	640 x 480
Dot Pitch	.25 mm
Viewable Picture Size	14 in.

Technical Features
Form Factor	Desktop
Resolutions supported	1024 x 768, 1280 x 1024, 640 x 480, 800 x 600, 832 x 624
Synchronization Range - Vertical	50 - 120 Hz
Synchronization Range - Horizontal	30 - 70 kHz
```

So, I guess my next move should be to define some additional parameters into xorg ?

Cheers

---

### Post by wieman01 on 2006-09-25
Mmm... I am afraid I won't be able to help you much as I don't know anything about your configuration, however, why don't you do this (after making a safety copy of you xorg.conf):

Edit current "Device" (add 2 lines):
> Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
[COLOR="Red"]Option	"MonitorLayout"	"CRT,LFP"
Screen 	0[/COLOR]
EndSection
Add second "Device":
> Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite" 
	Screen 		1
EndSection
Add second "Monitor":
> Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76
EndSection
Add second "Screen":
> Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    **[COLOR="Red"]24[/COLOR]**
        SubSection "Display"
                Depth           **[COLOR="Red"]24[/COLOR]**
                Modes           "800x600"
        EndSubSection
EndSection
[COLOR="Blue"]Here it is important to note that **"DefaultDepth"** of both screens must match i.e. have the same value.[/COLOR]

Change your current "ServerLayout" (add 2 lines):
> Screen	"External Screen" RightOf "Default Screen"
Option	"Xinerama" "true"
Now add 3 lines at the end of "xorg.conf":
> Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection
[COLOR="Blue"]Please post the contents of the new version of your xorg.conf file so that we can have a second glance at it and see if anything is wrong with it.[/COLOR]

You need to restart X after you have saved the changes.

---

### Post by Peacepunk on 2006-09-25
yep, let's give [COLOR="Sienna"]xinerama[/COLOR] a try.

If I think right, the above configs recommendations comes from your own, right ?

I saw <<800x600>> definition that I know will not suit, so I have to dig a bit further to check all parameters.

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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"MonitorLayout" "CRT,LFP"
	Screen 0
EndSection

Section "Device"
	Identifier 	"External Device"
	Driver 		"i810"
	BusID 		"PCI:0:2:0"
	Option 		"MonitorLayout" "CRT,LFP"
	Option 		"TVOutFormat" "Composite"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier "External Monitor"
	Option "DPMS"
	HorizSync 30 - 85
	VertRefresh 56 - 76
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
	Depth		1
	Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection
Section "Screen"
	Identifier "External Screen"
	Device "External Device"
	Monitor "External Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Screen 1 "External Screen" RightOf "Default Screen"
	Option "Xinerama" "true" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection
```

---

### Post by Peacepunk on 2006-09-25
Success !

Thanks Wieman: My Laptop is now umleashed to the full power of DualHead Capability.

My current Screen Def is a whopping 2304 x 768, seamlessly spread over two very different supports, the 1280 x 768 Widescreen Laptop LCD and external 15" 1024 x 768 Trinitron LCD.

Battery-wise, I am still able to shut down the vga output thanks to i810switch (no need to *sudo*)

```

i810swith crt off
```

sure,

```

i810switch crt on
```

puts the thing back online.

Now, for the drawbacks:

-Even with CRT off, the next screen still exists, so you can loose stuff on the other screen while on the go, unplugged to the external monitor, unable to retrieve them... Even worse, Ubuntu sometimes open up stuff in the next screen: additionnal file browser windows, Firefox fired on a link from a web page that makes it firing the link in n new instance.

**[COLOR="Navy"]Get it back is PitA: you can see in your desktop toolbar that something is on the wrong side; you must first check it's not plain screen, un-plain screen it if needed, then move your mouse in the invisible area, hold Alt-LeftClick+draw the window back into the laptop screen...[/COLOR]**

-As underlined by shaviro, there is no simple way of switching between single and dual mode here.

-plain-screen applications opens in Laptop Display (penguin-racer, for instance)

-geometry on CRT tends to be confused by the hack, so you need to play a bit with it for optimal results.

Nevertheless, when you think that this 2000+ USD baby came out of factory WITHOUT dualHead, you cannot feel anyhing but slightly satisfied by this hack. Soo good.

Clicking "Full Screen" button on a window put the said window in plain screen @ the correct size. Even F11 with GIMP gives you a full screen image from wathever screen the image is displayed on

Contents of Pictures Folders with thumbnails displays across the two screens

I am then happy to confirm this procedure to work with Vaio's subnotebook VGN-T17GP and VGN-16SP. Hardware is Intel Corporation 82852/855GM Integrated Graphics Device, on a 1,3kg subnotebook with Widescreen. Does exist in the rest of the world under different names, it's the 10.1 screen with 1.1 P4 & dvd player keys on upper right.

---

### Post by wieman01 on 2006-09-25
Great! And yes, I have given you my own settings (800x600) as I don't know what your configuration is. :-)

Good stuff, buddy. Keep us posted if you find any other solution.

N.B.: Try to replace "RightOf" with "Relative". Perhaps that's better for you. The full set of options is: RightOf, LeftOf, Below, Above, Absolute X Y, Relative.

---

### Post by Peacepunk on 2006-09-26
Thanks again

The laptop fits well underneath the CRT, so I was thinking of "TopOf" as in the same family as "RightOf": thanks for the "Above" tip.

One _**killing** drawback_ is that sometimes, stuff opens up in the "other" screen - unfriendly when unplugged, and let's face it: I'am unplugged to an external screen most of the time, target use is presentations, exhibitions, this kind of public stuff.

Does relative and absolute X Y have other parameters that you are aware of ?

Shall we summarize all this in a "**HowTo *Get Dual Head on 855GM with Xinerama***" ?

---

### Post by wieman01 on 2006-09-26
> **Peacepunk said:**
> One _**killing** drawback_ is that sometimes, stuff opens up in the "other" screen - unfriendly when unplugged, and let's face it: I'am unplugged to an external screen most of the time, target use is presentations, exhibitions, this kind of public stuff.
On my computer Windows open up in the very screen where the mouse pointer is located. Strange thing that is going on on your PC. Can't help you there.
> **Peacepunk said:**
> 
Does relative and absolute X Y have other parameters that you are aware of ?
I don't happen to know any other parameters. However, "Absolute X Y" stands for your screen's resolution i.e. the horizontal & vertical line. So try to play around with it.
> **Peacepunk said:**
> Shall we summarize all this in a "**HowTo *Get Dual Head on 855GM with Xinerama***" ?
I would like to. Can we change the name of the thread? Let me try...

---

### Post by wieman01 on 2006-09-26
Quick note: Tried to rename it but I have no idea how to do that... Any idea?

---

### Post by Peacepunk on 2006-09-26
It's been renamed, by the way, indeed it is.

Now for reader's convenience, my suggestion was to start another one, with title as "HOWTO get Dual Head on a 855g laptop with Xinerama"

Post shoud contain links submitted here, more commented generic Xorg.Conf with empty fileds where the user should put his own parameters and explanation of advantages & drawbacks + a query for other types of hardware found compliant with this method.

(I believe this to be very generic, and should work with a lot of other Laptops with VGA output.)

As I am the least computer-skilled guy among the two of us, I'd be happy to review the text & give detail oriented to the dumb user like me.

For general info, this link

[http://ubuntuforums.org/showpost.php?p=454217&postcount=1](http://ubuntuforums.org/showpost.php?p=454217&postcount=1)

should be added, along with

[http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)

(a modeline calculator)

At office hours, the desktop and its CRT is under havy use (I like SuSE93-KDE for work: It's a multimedia shame, but a grat workstation).
I'll get to twisting parameters a bit later.

---

### Post by wieman01 on 2006-09-26
Ok, shall we continue our discussion by mail? Willing to turn this around and give the howto a shot. Want to do this together?

---

### Post by wieman01 on 2006-09-26
Hello Peacepunk, 

No need to reinvent the wheel... This is all we need in a nutshell I guess:

[http://www.ubuntuforums.org/showthread.php?t=221174]("http://www.ubuntuforums.org/showthread.php?t=221174")

---

### Post by Peacepunk on 2006-09-26
[-( You say nutshell, I say it's Vogon Poetry to me [-(

In Computer world, some people truly looks they are coming from another arm of the galaxy to me.

Excellent link, indeed. I spotted it sometimes ago, and just cannot read it to the end...

Cheers, thanks again, guess we can close this one.

---

### Post by wieman01 on 2007-07-27
I am bringing this up again just to say that Ubuntu has improved a lot in the meantime. Connecting an external display in Feisty Fawn is a lot easier with a few simple steps given in this HOWTO:

[http://ubuntuforums.org/showthread.php?t=411674&highlight=external+projector+intel]("http://ubuntuforums.org/showthread.php?t=411674&highlight=external+projector+intel")

So Xinerama is no more necessary and there is no need to manually configure any sort of text file in order to enable the output.

---

### Post by Peacepunk on 2007-09-03
Thanks for the update.

I posted a link to this thread here though - I bet not everyone is jumping on every new Ubuntu release...

Bye

---

### Post by wieman01 on 2007-09-03
> **Peacepunk said:**
> Thanks for the update.

I posted a link to this thread here though - I bet not everyone is jumping on every new Ubuntu release...
Guess so... but Feisty has been a real improvement. I liked Dapper a lot, but Feisty has made life a lot easier if you know what I mean. :-) Give it a try when you have the time.

---

### Post by wildpatel on 2007-09-08
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Option    "MonitorLayout" "CRT,LFP"
        Option    "Clone" "true"
        Option    "DevicePresence" "true"
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
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


This is the xorg info. 

Im getting the 

> wildpatel@wildpatel:~$ i810switch crt on
PCI id of i810 is not recognized.


And i dont know what to do please help..really new to linux/ubuntu...but quick to learn..please help.

---

### Post by wieman01 on 2007-09-09
@Wildpatel:

First off what hardware have you got and what version of Ubuntu are you on?

---

