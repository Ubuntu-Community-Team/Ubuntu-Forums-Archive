---
title: "ATI Mobility Radeon 7500 - how to improve performance"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-04-12
i'm the (unlucky?) owner of a laptop with an ATI Mobility Radeon 7500 graphics chip. 2d graphics in Gnome operate in a somewhat laggy, cumbersome manner. one can feel that it's not performing at its full capacity when dragging windows, resizing them, launching menus, and most important of all, drawing of newly launched application windows. 

since this device isn't supported in fglrx, is there another driver package i should install to improve general graphics performance? will the usual ATI drivers work with Mobility devices as well? i'd appreciate if you can point me to the latest version of the most appropriate driver for this chip, and/or any tweaks i should perform (perhaps in xorg.conf) that may help boost performance.

also, this device is listed as Mobility Radeon 9000 in my xorg.conf ; is this usual?

thanks!

---

### Post by Qdlaty on 2005-04-12
Hi,
I have ATI Radeon 7000 in my notebook and it's also described as 9000 M6 so don't worry.
Add those three lines to your Device Section:
	Option 		"AGPMode" 		"4"
	Option 		"AGPFastWrite" 		"True"
	Option 		"EnablePageFlip" 	"True"
and restart whole Xs.
It may help a little.
The other solution is to purchase AcceleratedX. It really gives a bust but it costs ~100$ so I don't know if it's worth.
Please also consider changing window manager to less resource consuming one.
I use Enlightenment and I'm damn happy with it.

---

### Post by 23meg on 2005-04-12
thanks, i already have those lines in xorg.conf, and they seem to have helped exactly as you've described: "a little" ;)

i hadn't heard of accelerated x, i'll look into it now. i'm also considering switching to XFCE altogether. i hope their new file manager comes along quickly and nicely.

---

### Post by Qdlaty on 2005-04-12
Accelerated X you may find at: [www.xig.com](http://www.xig.com) 

Have you ever tried ROX-Filler (you may also then try whole ROX window management environment: ROX-Session etc.).

But I agree, XFCE is a good choice.

How much FPS your glxgears shows?

---

### Post by 23meg on 2005-04-12
looks like accelerated x doesn't support this card.

i did work with ROX filer but i think they're developing a new file manager that is a kind of ROX - Nautilus hybrid.

in glxgears i get between 1100 - 1400 fps. i don't think this indicates anything related to 2D performance though.

---

### Post by NTolerance on 2005-04-13
I've got a Mobility M6 chip in my laptop which I *think* is supposed to be equivalent to a 7500.  Can anyone confirm this?  It's fast enough in KDE but I seem to get stuck exactly at 377fps in glxgears for some reason.  I have enabled all of the xorg.conf tweaks.  What gives?

---

### Post by Qdlaty on 2005-04-13
Accelerated X supports it as well as mine 7000. I checked it long time ago.
Annyway, it is damn hard to install since it comes only with rpms!
If you like candy filemanagers try Evidence ;-)
I've ~550 FPS at my 7000, it was only my cuoriosity, it don't have any thing to do with 2D.
I don't know what makes you think that your 2D performance is weak - describe - are windows drawing noticeably?

M6 is a codename for 7x00 serie (mostly for 7000 - my is M6T).

---

### Post by 23meg on 2005-04-13
but none of the mobility chips are listed in the accelerated x page as supported.

i'm having laggy updates in overlay windows, and it takes more time than it should to draw newly opened windows, that's all for now. disabling powernowd altogether and enabling prelinking has improved overall performance noticeably for me.

by the way, is my glxgears score a good one? i haven't gone into 3D stuf at all in Linux so far so i don't know. i think 3D hardware acceleration isn't enabled by default; how do i go about enabling it with this device without fglrx?

---

### Post by 23meg on 2005-04-14
and is there a (perhaps updated) driver package i should install, in the repositories or elsewhere?

---

### Post by NeoChaosX on 2005-04-14
Try installing the [DRI](http://dri.freedesktop.org/wiki/) drivers and see if that helps any. It boosted my scores a bit (although the tips in this thread have boosted them even higher).

---

### Post by NTolerance on 2005-04-14
[QUOTE=NeoChaosX]Try installing the [DRI](http://dri.freedesktop.org/wiki/) drivers and see if that helps any. It boosted my scores a bit (although the tips in this thread have boosted them even higher).[/QUOTE]

I would strongly recommend using the [Debian packages](http://dri.freedesktop.org/wiki/Download#head-0578b19757b79fb1eed3812b628ec6746db4478b) when trying to update the DRI drivers.  I attempted to compile them from source yesterday and got all sorts of cryptic compiler errors that don't mean anything to anybody.  Installing the Debian packages isn't easy either though - they are dependent on several other packages and errors will pop up about the packages not being able to overwrite some of the installed xorg files.  I did some Googling and the 2nd to last suggestion on [this page](http://www.mepis.org/node/2947) helped me to get the packages installed.

Also, at the end of the DRI installation it will ask if you want to compile some stuff for S3TC support.  I could never get this to work, so I had to uninstall and run the setup again without S3TC support.

---

### Post by 23meg on 2005-04-14
thanks, where can i get them?

---

### Post by NTolerance on 2005-04-14
[QUOTE=23meg]thanks, where can i get them?[/QUOTE]

[http://dri.freedesktop.org/wiki/Download#head-0578b19757b79fb1eed3812b628ec6746db4478b](http://dri.freedesktop.org/wiki/Download#head-0578b19757b79fb1eed3812b628ec6746db4478b)

---

### Post by NeoChaosX on 2005-04-14
I wouldn't try installing the Debian binaries - when I did, they hosed my Xorg server and the OpenGL drivers. Luckily, I only needed to reinstall them in apt, but I'm doing better compiling from source. Use the binaries at your own risk.

---

### Post by benplaut on 2005-04-17
bumpity bump  :) 

i also am the owner of a aging Radeon Mobie 7500... and am a bit confused by 3D support. I am coming from a brief background of SuSE 9.2, in which SAX2 was a GUI way to enable 3D. Now, with ubuntu, i am stuck with a xorg.conf that i can't exactly figure out.

Will the tips in this thread enable 3D? 

Thankee  :razz:

---

### Post by ghaspias on 2005-04-24
[QUOTE=Qdlaty]Accelerated X supports it as well as mine 7000. I checked it long time ago.
Annyway, it is damn hard to install since it comes only with rpms!
If you like candy filemanagers try Evidence ;-)
I've ~550 FPS at my 7000, it was only my cuoriosity, it don't have any thing to do with 2D.
I don't know what makes you think that your 2D performance is weak - describe - are windows drawing noticeably?

M6 is a codename for 7x00 serie (mostly for 7000 - my is M6T).[/QUOTE]
 I have followed the Ubuntu distribution with a great interest, using the live cd. Now I finally installed the hoary 5.04, and have had many problems :-(
The most unexpected is the ridiculous 2d performance: my windows leave large trails when I drag them, lasting for about 1 second!! It doesn't 'feel' slow, it is dauntingly, painfully slow!!
I didn't notice that kind of problem in the live cd...
I have a Asus L3C laptop with an ATI Mobility Radeon 7500.
Any tip on what the problem might be?

---

### Post by Qdlaty on 2005-04-24
Hi,
long time no seen.
I've changed distro into Arch (I'd my Ubuntu broken nicely so I though, why not).
Annyway,
did you tried to follow ours tips with xorg.conf ?
You may send me (PM, e-mail) yours and I'll take a look.

Bye now.

---

### Post by ghaspias on 2005-05-03
Hi Qdlaty...
Have we met before? I don't remember, but thanks for the warm salutation!

I have followed the tips and it did make some difference. I noticed that the excessive  (several seconds) lag in border redraws happens only in some circunstances - namely when dragging a window in front of firefox. So, the problem might be more specific. I am reasonably happy with my Mobility 7500's performance now. Still, I hope this will be better supported by default in the future - there should be an gui for twaking this, as for many other little bits that might be disabled by default because the installer can't do it all. The user should be offered the option to fine-tune the system, if he is interested, even if he is not an expert.

This is in my opinion the biggest flaw in this distro: I don't want another cripple-ware OS à la Microsoft. And altough you can still do pretty much anything in Ubuntu, via the CLI or editing config. files, a modern OS shouldn't rely solely on a CLI interface for a large number of administrative tasks.

Look at MacOS: there is very little a common user will ever need to do via a prompt. The choice between a gui and a cli should be a matter of taste, not a trade-off between usability and flexibility/maintenance...

---

### Post by NTolerance on 2005-05-03
[QUOTE=ghaspias]Hi Qdlaty...
Have we met before? I don't remember, but thanks for the warm salutation!

I have followed the tips and it did make some difference. I noticed that the excessive  (several seconds) lag in border redraws happens only in some circunstances - namely when dragging a window in front of firefox. So, the problem might be more specific. I am reasonably happy with my Mobility 7500's performance now. Still, I hope this will be better supported by default in the future - there should be an gui for twaking this, as for many other little bits that might be disabled by default because the installer can't do it all. The user should be offered the option to fine-tune the system, if he is interested, even if he is not an expert.

This is in my opinion the biggest flaw in this distro: I don't want another cripple-ware OS à la Microsoft. And altough you can still do pretty much anything in Ubuntu, via the CLI or editing config. files, a modern OS shouldn't rely solely on a CLI interface for a large number of administrative tasks.

Look at MacOS: there is very little a common user will ever need to do via a prompt. The choice between a gui and a cli should be a matter of taste, not a trade-off between usability and flexibility/maintenance...[/QUOTE]

I agree.  Ubuntu was smart enough to enable DRI out of the box for my ATI Mobility M6, so it should also have been smart enough to turn on the features in xorg.conf that really make it work well.  There should be GUI options for these things.

---

### Post by 23meg on 2005-05-15
i've installed [Cube](http://www.cubeengine.com), and i'm getting spectacular performance from it, 26-30 fps in 1400x1050 resolution, totally smooth gameplay. however, [Flightgear](http://www.flightgear.org) runs at something like 5-6 fps; it seems there's no standard system-wide way of getting good 3d performance.

any more 3d tips for this card? any Flightgear tips? any more suggested free 3d apps / games to test performance with?

---

### Post by 23meg on 2005-05-23
update: adding the "UseInternalAGPGART" "no" option to the device section of my xorg.conf seems to have increased frame rate in flightgear a bit, but it's still not satisfactory. glxconfig reports that i have direct rendering enabled, but flightgear is still suffering..

---

### Post by ghaspias on 2005-10-29
Almost 6 months have gone by, I am now using Breezy, and the issues I reported earlier are still there. I can paint my screen with a window - when I drag any window, it leaves a trail of damaged regions that take up to 1 or 2 seconds to be updated.
I have tried several tips found on these foruns, but couldn't get decent 2d redrawing.
This isn't a show stoper, but it puzzles me - how come my graphics card can draw 700 frames per second and still takes 1 second to redraw my windows?!

I was hoping these kind of problems to go away OR to have an 'official' explanation.

I am using an Asus L3c with an ATI Mobility Radeon 7500 (M7), on a P4M @1700MHz.  The screen is set to 1400x1050, 24bit.

---

### Post by 23meg on 2005-10-30
[QUOTE=ghaspias]
This isn't a show stoper, but it puzzles me - how come my graphics card can draw 700 frames per second and still takes 1 second to redraw my windows?!
[/QUOTE]

You'll find the answer to that [here]("http://dri.freedesktop.org/~jonsmirl/graphics.html").

---

### Post by Arabian on 2007-04-24
Any updates on on performance? or we aren't lucky yet?

---

### Post by BungaMan on 2007-04-24
I posted a little howto.  It could be worth a few extra frames

[http://ubuntuforums.org/showthread.php?t=396671](http://ubuntuforums.org/showthread.php?t=396671)

---

### Post by kaede on 2007-04-25
are this card support for running beryl? 


i have the same problem here 2. using mobility radeon 7500 on asus l3c. seems like a lil bit lagging on navigation. anyone can manage running beryl with this graphic card?

please help me :D

thanks

---

### Post by UrbenLegend on 2007-04-27
I have a Dell Inspiron 5100 with a mobility radeon 7500 and I have it running well with the Mesa drivers under Feisty Fawn but there is some corruption. In some programs, 3D elements are sometimes garbled or missing. For example, the Quake III main menu logo doesn't appear. The tremulous logo during gameplay doesn't appear. The Blender interface is practically unusable. I started to have this issue with the Mesa 6.5.2 drivers. The 6.5.1 Mesa drivers seem to work perfectly with 3D apps, but I have qualms about reverting it to this version because then beryl and compiz break while all the regular 3D programs function normally. Anyone know what's wrong?
The performance is alright for me, its just that the 3D stuff sometimes don't display properly.

Help appreciated.

---

### Post by kaede on 2007-04-28
so it mean that ATI Mobility Radeon 7500 is able tu running beryl right ?

---

### Post by UrbenLegend on 2007-04-29
Yes quite well actually. Except if you turn on blur for that vista like effect or if you decide to play videos using the XVideo extension. The blur creates artifacts if its set to blur even during window movement. Any videos played with the XVideo extension creates a blank screen. But other than that its surprisingly snappy.

---

### Post by kaede on 2007-04-29
could u share us your xorg.conf please :D

---

### Post by UrbenLegend on 2007-04-30
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
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "AGPSize" "32"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
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
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

There you go, have fun. But have any of you guys experienced problems with the 6.5.2 Mesa drivers?

---

### Post by kaede on 2007-05-02
thanks mate, i never tought your xorg.conf would be that simple. :D
especially on the device section.
i'm actually using 6.5.2 mesa driver. so far so good.what kind of problem do u encounter?

---

### Post by mmatt on 2007-05-02
I also have a Dell inspiron 5100 with Mobility Radeon 7500. Beryl is very useable (most of the time), especially if you're just after the basic useability plugins (scale, desktop cube, window switching, etc.). Stay away from the blur, it's evil. Animations work o.k. with the right settings (timestep, speed). Biggest setback for me at the moment is Blender. It worked fine under openSuSE, but switching to feisty broke it. Almost everything else is better though, so I'd really like to stick with it.

Any ideas on fixing Blender? Please?

I'm currently using the "ati" driver WITHOUT beryl (even though it's good, I prefer a slick interface).

Tried a few suggested xorg.conf changes, the best ones being (in my experience):

Option "EnablePageFlip" "true"
Option "AGPMode" "4"

glxgears gives ~700 fps (not great, does anyone with this card get better?? if so which driver!)
open arena very playable
neverwinter nights is good on low graphics
All in all very happy, but want Blender to work! (have tried 2.42 and 2.43)

Matt

---

### Post by mmatt on 2007-05-02
Ok, managed to make some serious performance increase in glxgears (~1700). Still haven't got Blender working!

Here's what I did:

1) Changed device section of /etc/X11/xorg.conf
     Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "EnablePageFlip"        "true"
        Option          "AGPFastWrite"          "true"
        Option          "EnableDepthMoves"      "true"
        Option          "GARTSize"              "64"
        Option          "AGPSize"               "64"
        Option          "backingstore"          "on"
        Option          "UseInternalAGPGART"    "no"
     EndSection

2) downloaded driconf (sudo apt-get install driconf). Enable HyperZ (Big improvement)

3) changed the default colour depth to 16 (another big difference, not noticeable in quality):
     Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
     .
     .etc

Anyone getting better than ~1700 fps in glxgears (I know it's not a great benchmark but it does give an indication).

More importantly, has anyone got Blender to work in ubuntu feisty with this driver?

Matt

Edit: dropping to depth 16 made some SDL games (namely Neverwinter Nights) unplayable. Don't let glxgears be the only reference!

---

### Post by UrbenLegend on 2007-05-02
Does Blender look hopelessly garbled? Cuz that's one of my problems with the 6.5.2 driver. Practically unusable cuz all the buttons disappear. Also the 6.5.2 driver doesn't display the Quake III logo whenever I play the game and some of the HUD disappears also. Those are my main issues.

openSUSE runs Blender well because it has the old 6.5.1 drivers. You'll find that if you upgrade to Xorg 7.2 (which has the Mesa 6.5.2 drivers) on opensuse, Blender will break (at least in my experience). But what is your problem with Blender? I want to confirm whether we're having the same problem.

Also using AGPSize "64" causes maximized windows to have a completely white titlebar. I use AGPSize "32" instead.

---

### Post by kaede on 2007-05-03
my glxgears is around 900 fps. currently. but since im stilll using compiz. so i dont really know about blender afterall. 

im interested with driconf , is it really make a big improvement on the frame rate?

what makes the different using "ati" and "radeon" ?

coz im currently using "radeon" 

thanks

---

### Post by kaede on 2007-05-03
wow, you're rocks man. with just installing driconf i get a little bit improvement on fps.

but after changing the screen depth into 16. my fps became doubled around 1500-1600 fps.
even though i don't really like the screen collor .

here i'm sharing my xorg.conf.


```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "True"
	Option "EnablePageFlip" "True"
	Option "AGPSize" "32"
	Option "DRI" "true"
	Option	"EnableDepthMoves" "true"
	Option	"AccelMethod" "XAA"
	Option	"NoAccel" "False"
	Option		"XAANoOffscreenPixmaps"
	Option		"ColorTiling"		"on"
	Option		"RenderAccel"		"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option       "AIGLX"   "true"
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

Section "Extensions"
        Option  "Composite" "enable"
EndSection
```

---

### Post by UrbenLegend on 2007-05-03
ati is the proprietary opengl driver provided by ati. You use the fglrx driver option to use this. radeon is the open source implementation based on DRI and the Mesa libs. For older cards like the 7500, the opensource drivers support the card better.

---

### Post by mmatt on 2007-05-04
I'm not sure how accurate that is (about ati being the proprietary driver). From what I understand, fglrx is the proprietary driver and I used man radeon when setting options for ati. I'm not sure if I'm right on this or not, I would gladly be corrected. (also, from what I understand, fglrx doesn't support our video card)

As for blender, it runs, but the interface is very stange! The buttons disappear, the top 25% of the screen is somewhat garbled, the buttons in the bottom appear when the mouse is over them, appear if their 'window' titles are selected. It is only useable (somewhat) because I know my way around.
[http://people.bath.ac.uk/mpw20/media/snapshot1.png](http://people.bath.ac.uk/mpw20/media/snapshot1.png)

Also, I haven't noticed any problems with 64 gart size, but I shall keep my eyes peeled. driconf made a huge difference (hyperZ and software TCL). depth 16 works for some apps but not for others, haven't really found a pattern, but SDL apps seem to prefer 24 default.

I didn't upgrade Xorg in openSuSE, but then 3D performance was not great in that distro, I was pleasantly surprised moving to Kubuntu feisty!

Still no luck with blender, it's the last thing left to fix..... ( apart from suspend to disk aka hibernate, which hasn't worked in any distro).

Matt


from "man ati":

ati  is  an  Xorg  wrapper  driver for ATI video cards.  It autodetects
       whether your hardware has a Radeon, Rage  128,  or  Mach64  or  earlier
       class  of  chipset,  and  loads  the  radeon(4), r128(4), or atimisc(4)
       driver as appropriate.

---

### Post by UrbenLegend on 2007-05-04
My Blender is exactly like that!!! You hit the nail on the spot.

If you had upgraded Xorg and Mesa, Blender would have looked horrible in openSUSE too. I don't know how to fix the Mesa 6.5.2 drivers so they work properly however. A shame really, I would have liked experimenting with Blender on my laptop.

---

### Post by kaede on 2007-05-05
i know it seems a little bit out of topic, but can u tell me how to manage temperature in ubuntu?

seems like my notebook getin too hot while im running ubuntu. (60-70 celcius) and when it's really hot.
my graphical performance seems lagging. all the windows grabled when im dragging in all over.

---

### Post by mmatt on 2007-05-05
Well, I'm not sure about your Asus. On my Dell there's dellfand, a daemon which takes over fan control from the bios. There may be something similar for your laptop. Also, Dell "solved" a major overheating problem on this model (i5100) by releasing a bios update (I'm currently running A32), which altered the thermal management. I don't use dellfand but have tried it and know that it works on this model.

If the blender problem is with the Xorg driver I will look around for a solution there. I had thought the problem was with feisty, but so far all problems have been driver related (either too old or, now, too new!)

Matt

---

### Post by mmatt on 2007-05-05
An interesting development....

Setting Option "NoAccel" "yes" in xorg.conf makes blender work perfectly. It does however ruin everything else. Is there a way of setting application specific rendering (i.e. use accel for everything, except this)? Any thoughts?

Matt

---

### Post by kaede on 2007-05-05
beside EXA i'm actually using XAA as my accel method. why don't u try it .

---

### Post by mmatt on 2007-05-06
I'm currently using XAA although I did try EXA. Neither solved the problem. I've found others who agree that the updated Mesa drivers are the cause. I tried to compile the development version from source but encountered lots of errors due to missing headers. I'm being lazy using adept and apt-get and couldn't work out which packages I needed. Also, I don't know that it will solve the problem, whereas reverting to the earlier driver might.

As it stands I've written a script to edit my xorg.conf file wihch I can run and then restart X whenever I want to use blender (which, to be fair, isn't that often). Not ideal, but I'm willing to wait until better drivers come out or I build a desktop in the summer. Is the blender problem related to this ati card or is everyone with Mesa 6.5.2 having problems?

Matt

---

### Post by kaede on 2007-05-06
since i'm not using blender so i can't give any input for you mate. but so far my system running compiz quite stable. even tough with just p4 1,7GHz, 384MB and ATI 32MB. now that i'm getting curious what is this blender thing :p

---

### Post by mmatt on 2007-05-06
Lol, what is this blender thing? Blender is an open source 3d modeling/animation/post production program similar to commercial products like Maya or 3d Studio Max. It's really very easy to use, with a couple of tutorials I was well on my way to making projects of my own, purely for the enjoyment of exercising my imagination and creativity. All in all, it's great fun. Good luck with the ati card :) . I'm hoping to be rid of it as soon as possible, bring on nVidia SLi... (when I've worked my **** off this summer).

---

### Post by kaede on 2007-05-07
whoops my bad. i tought blender is one of the effect from berly. :p. anyway good luck with the project. :D

---

### Post by mmatt on 2007-05-09
Another good option:

Option          "ColorTiling"           "on"

Adds some serious boost to glxgears.

Matt

---

### Post by kaede on 2007-05-09
i do put that option on my xorg.conf anyway :D.
 any other tweaks for this card maybe? :D

---

### Post by bgryderclock on 2007-05-13
> **mmatt said:**
> An interesting development....
[B]
Setting Option "NoAccel" "yes" in xorg.conf makes blender work perfectly[/B]. It does however ruin everything else. 

Matt

Nice! That worked for me! <3

---

### Post by shak541 on 2007-08-22
thank you to everyone. After these tweeks my ATI card performs alot better. Before it lagged with fading and drop shadows and transparent windows and now it doesn't lag too much. Transparent windows work about 2 times better while dragging for some reason. Fading is now perfectly smooth and drop shadows dont really drop performance at all. Thank you to everyone! :D

---

### Post by mmatt on 2007-08-23
I'm glad to hear you've found what you needed, it's always good for people who post tips to get some feedback.

---

### Post by gijoe3k on 2008-01-01
> **mmatt said:**
> Ok, managed to make some serious performance increase in glxgears (~1700). Still haven't got Blender working!

Here's what I did:

1) Changed device section of /etc/X11/xorg.conf
     Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "EnablePageFlip"        "true"
        Option          "AGPFastWrite"          "true"
        Option          "EnableDepthMoves"      "true"
        Option          "GARTSize"              "64"
        Option          "AGPSize"               "64"
        Option          "backingstore"          "on"
        Option          "UseInternalAGPGART"    "no"
     EndSection

2) downloaded driconf (sudo apt-get install driconf). Enable HyperZ (Big improvement)

3) changed the default colour depth to 16 (another big difference, not noticeable in quality):
     Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
     .
     .etc

Anyone getting better than ~1700 fps in glxgears (I know it's not a great benchmark but it does give an indication).

More importantly, has anyone got Blender to work in ubuntu feisty with this driver?

Matt

Edit: dropping to depth 16 made some SDL games (namely Neverwinter Nights) unplayable. Don't let glxgears be the only reference!

MMatt, If I ever meet you in person someday I will personally buy you a beer(or whatever you drink :) I have been trying to get my Radeon Mobility 7500 to get past 765fps on glxgears for the past few days. Your suggestion for the driconf program saved the day, i  now get 1200fps in glxgears. You rock man!!

---

### Post by mmatt on 2008-01-01
Beer's fine by me. I should mention that, as with most things in Linux, I didn't work all that out by myself. A mixture of forum gleaning and trial and error on the most part.

Some sad news I'm afraid... (Well good news actually). Having finally scraped together some funds I've built a shiny new desktop and am therefore neglecting the old Dell i5100 and it's ATi mobility graphics card...

Glad this thread's been useful gijoe3k.

---

### Post by visionary on 2008-01-13
With reference to Flightgear performance and video rendering (frame rate)

Maybe you could try the following which i harvested from some other websites which helped me greatly with Flightgear in Gusty....

1)When you start flight gear, consider starting with the following options in your command.... (You can read more from here [http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html](http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html) )

> --control=mouse
> --disable-intro-music
> --disable-random-objects
> --disable-sound
> --disable-hud-3d
> --disable-specular-highlight
> --fog-fastest
> --model-hz=60
> --geometry=800x600
> --visibility=10000.0
> --fov=50
> 
> --prop:/sim/rendering/static-lod/detailed=500
> --prop:/sim/rendering/static-lod/rough=5000
> --prop:/sim/rendering/static-lod/bare=15000
> --prop:/environment/clouds/layer[1]/coverage="clear"
> --log-level=alert

That actually improved a little.....Now for the biggest improvement i go was to to do the following.....

2) downloaded driconf (sudo apt-get install driconf)

3)Then edit device section of /etc/X11/xorg.conf to show as

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
[B]BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"[/B]
EndSection


Though i am using Nvidia card, i added those lines (in bold)  in my xorg.conf file.

Now restart your system and enjoy your flight gear.
Hope that helps!

Cheers!

---

### Post by oldsmobile_mike on 2008-02-11
Thanks for the tips, everyone!  I will say that making the xorg.conf changes only resulted in about 5-10 more fps in glxgears, but that installing driconf with HyperZ resulted in an improvement of about 350 fps (currently getting around 1415-1420 fps, I believe that would go up again if I dropped down to a 16 bit display, but I do graphic design and watch movies on my computer, besides the occasional game, so would rather keep it at 24 bit).

Thanks!

---

### Post by oldsmobile_mike on 2008-02-12
As a side note, those changes to xorg.conf wound up messing up my screensaver - it was dim and flickery, almost like it was dropping frames, or something.  Tried different screen savers but it was the same with all of them.  Took the xorg changes out, and screensaver was back to normal.  Weird!  Oh well, no loss, the changes barely made a difference, anyway.

---

### Post by jdix123 on 2008-02-15
Hey you're guys' tips were great -- got my desktop effects enabled (where I couldn't figure out how before) and let me use compiz and awn.

Weirdism:  I setup up and configured my xorg.conf to where it was working well.  I enabled desktop effects and dl/ed compiz fusion.  I set up the effects to my liking (transparency, cube, etc.), and installed awn.  Hooray!  Everything was working.  Through reboots.

Now when I try to use the xorg.conf file (no change) it crashes the x server when I boot.  Rather than my gnome splash I get a blinking cursor.

A) what might be causing this, and 
B) why would it work fine for four or five boots and then suddenly stop when as far as I can tell, nothing changed.

---

