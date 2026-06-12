---
title: "[deb] xserver-xorg-video-intel_2.1.0-1ubuntu1_amd64 feisty backport"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by JoSch on 2007-07-14
Mostly inspired by [this post](http://ubuntuforums.org/showthread.php?t=494943) by Voland666 and with great help of [prevu](http://ubuntuforums.org/showthread.php?t=268687) I managed to backport the intel video driver from gutsy to feisty 64bit as requested by some useres in Volands thread.

Unlike the i386 version by Voland my backport depends on xserver-xorg-core_1.3.0.0 which I also added as a backport from gutsy to feisty as a simple deb.

The compile took hours on my 2GHz Core2 Duo because I also had to compile the whole xserver stuff but I think it was worth it because the graphics on my Dell D830 with X3100 graphics are crisp and sharp now. Even 3D acceleration works - 830fps with glxgears.
You will also have to uninstall xserver-xorg-video-i810 beforehand because it conflicts with the new driver.

I had to upload the files on my website [johannes-schauer.de](http://johannes-schauer.de/viewtopic.php?f=29&t=253) (german) because the xserver-xorg-core package was too large to upload on ubuntuforums. Here are the Links:
[xserver-xorg-core_1.3.0.0.dfsg-6ubuntu2~7.04prevu1_amd64.deb](http://johannes-schauer.de/download.php?id=423&f=29)
[xserver-xorg-video-intel_2.1.0-1ubuntu1~7.04prevu1_amd64.deb](http://johannes-schauer.de/download.php?id=424&f=29)

**Step-by-step:**
- Download both deb packages to your home folder then
```
sudo apt-get remove xserver-xorg-video-i810
sudo dpkg -i xserver-xorg-core_1.3.0.0.dfsg-6ubuntu2~7.04prevu1_amd64.deb
sudo dpkg -i xserver-xorg-video-intel_2.1.0-1ubuntu1~7.04prevu1_amd64.deb
sudo dpkg-reconfigure xserver-xorg

```
- choose intel as your driver in dpkg-reconfigure
- enjoy!

Let me know if it worked for you!
Have fun! JoSch

P.S.: As Voland did I added a poll to this thread.

EDIT: Hell it works so nicely - I was just playing starcraft for an hour and it was excellent smooth! But I should consider trying more graphic hungry applications. :-D

---

### Post by gummibaerchen on 2007-07-14
Wow, thank you sooo much!!!

I just got my new laptop with X3100 yesterday.

graphic was super with gutsy, but gutsy is just to unstable.

and now 64bit packages for feisty, thanks :)

you're my hero of the day :) :) I think I owe you a "Weißbier" ;)

---

### Post by JoSch on 2007-07-14
I'm just facilitated, that I'm not the only one my packages worked for. :)
Just wondering where you find the "ß" on an non-german keyboard... :shock:
EDIT: Don't mind... just recognized your username... ^^

---

### Post by davidmorawski on 2007-07-14
JoSch, it worked like a charm! Thank you so much for making this available. I don't play many games, but the choppy gradients I was experiencing before were starting to get on my nerves...

Another reason to love Linux; thanks again!

Dave

---

### Post by gcarrillo on 2007-07-14
Thanks, JoSch!

---

### Post by ifinishwhatistar on 2007-07-17
The driver installed fine and eliminated banding issues, but for me beryl still crashes whenever using any of the 3D effects.  Does anyone else have Beryl running OK with this driver?

---

### Post by JoSch on 2007-07-17
Notice [this thread](http://www.ubuntuforums.org/showthread.php?t=349732) in the Absolute Beginners area.

Problems with Beryl/compiz Fusion are better put in their forums because as it said: the software is BETA! Many users dont seem to realize this and get blended by fabulous youtube videos and expect a fully stable software but atm compiz fusion is NOT for a productive environment.

Btw: I was able to start compiz fusion but had to disable all funky effects. I think this problem is not only because Compiz is beta but also because the intel driver is not quite mature too - there is a reason for it not to be in the official feisty repositories. And now think about what happens when you put Beta and Beta together... :)

---

### Post by Syke on 2007-07-18
I would like to know why it's not in the official Feisty repos. The Intel driver is quite solid in Gutsy.

---

### Post by JoSch on 2007-07-18
Didn't you just complain about failing 3D [here](http://ubuntuforums.org/showpost.php?p=3038147&postcount=28)?
The driver is NOT very stable - a lot of people are demanding it but I dont think it would be a good idea atm -> the ubuntuforums would be flooded with bugs and crashes of their X3100 hardware.

---

### Post by System16 on 2007-07-30
Thank you so much for posting the 64-bit version, my screen is now so beautiful!!!!  THANK YOU!!

---

### Post by cacycleworks on 2007-08-01
YES!! 

Instant download thanks to your very fast server and easy install. On my Dell D630, when reconfiguring the xserver, "special" options I picked were no entry for video memory, didn't use frame buffer, "medium" setting -> 1440x900@100hz (only choice). And I never let it detect anything. 


To compile all that, you downloaded the -dev packages for xserver-core and -intel ?? It's "just like that" ? (is anything that easy)

Thanks, very appreciated! 
Chris
:KS

---

### Post by davidmorawski on 2007-08-15
Any idea if Xinerama can be used with this driver? If I add
```
Section "ServerFlags"
       Option          "Xinerama"      "true"
EndSection

```to my xorg.conf, X crashes (fatal server error).

Has anyone had any luck with a dual display?

---

### Post by JoSch on 2007-08-15
did you everything according to this tutorial: [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624) ?

---

### Post by davidmorawski on 2007-08-15
> **JoSch said:**
> did you everything according to this tutorial: [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624) ?
I did follow that tutorial--but with no luck. When I tried the incremental approach (ie., not just revamping my xorg.conf completely) and just added the Xinerama ServerFlag, X wouldn't start.

I'm beginning to think a dual display is not possible with the x3100 GMA...however, that can't be true unless it has to do with the Linux support since (here comes the most depressing part) **I was able to configure a dual display in about 5 second in Windows XP**.

---

### Post by JoSch on 2007-08-16
maybe you did something wrong?
theoretically it has to be possible.
display configuration is a pain on all linux distributions up until now. fortunately xorg7.3 arrives soon and gutsy will use it - no more xorg.conf file and dual montitor configuration by on the fly autodetection or a single click in a new configuration utility.
maybe you should burn a gutsy preview cd and try it out?

---

### Post by davidmorawski on 2007-08-16
Did I mention I'm using Feisty? Perhaps that has something to do with it...

I will try out Gutsy soon--but it won't be for another few days due to a cross-state move.

Thanks for throwing ideas out there, JoSch. Much appreciated :)

Dave

---

### Post by Buddy Gurt on 2007-09-01
This is super! No more blurryness, all colors are smooth! My screen is nearly perfect now, it almost hurts my eyes.
By the way, I'm using an HP 6710b with Intel T7500 and onboard video.

---

### Post by kao on 2007-09-09
The driver works great. But it seems there is lack of font smoothing :(

---

### Post by luzdegas on 2007-09-12
Hi!
I have the following problem. I have installed the 64 bit version of the drivers. Now the option 1440x900 (wich is the resolution I looked for) is available, but when I choose it, the "aspect ratio" is not ok. The screen look "shrinked". This does not happen when I choose other resolution (for example, 1400x1050), but my monitor (a Viewsonic 19" wide 1935wv) recommends the former one. I have no idea of what is going on... any suggestion?
Thanks in advance!

---

### Post by cacycleworks on 2007-09-12
> **luzdegas said:**
> Hi!
I have the following problem. I have installed the 64 bit version of the drivers. Now the option 1440x900 (wich is the resolution I looked for) is available, but when I choose it, the "aspect ratio" is not ok. The screen look "shrinked". This does not happen when I choose other resolution (for example, 1400x1050), but my monitor (a Viewsonic 19" wide 1935wv) recommends the former one. I have no idea of what is going on... any suggestion?
Thanks in advance!

Monitors work best at their "native resolution". perhaps that's the cause of the effect you're seeing?

---

### Post by luzdegas on 2007-09-12
The problem is that 1440x900 is the native resolution for this monitor.

---

### Post by bluenote on 2007-10-30
Hello !

(firstable, sorry for my english, i'm french) 

My OS is : Debian Lenny (testing) AMD64

Hardware

Motherboard Asus P5K-VM chipset G33/ICH9
Cpu : Intel Q6600 g0
Screen : ViewSonic P95f

My only problem is my screen's resolution : only 1280x768 (in spite of "1920x1440" "1856x1392" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480" 
24 bit)

I tried to install '915resolution' (0.5.3-1)

My config :

> 15:05 bluenote@Achille ~% cat /etc/default/915resolution
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=4b
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1600
YRESO=1200
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=16


> 15:07 bluenote@Achille ~% sudo 915resolution -l
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: G33
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


I tried to install :

xserver-xorg-core_1.3.0.0.dfsg-6ubuntu2~7.04prevu1_amd64.deb
xserver-xorg-video-intel_2.1.0-1ubuntu1~7.04prevu1_amd64.deb

but there is no effect, i'm always at 1280x768 !

My xorg :

> Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82G33/G31 Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "P95f+-2"
        Option          "DPMS"
        HorizSync       30-111
        VertRefresh     50-180
        Gamma           1 1 1
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82G33/G31 Express Integrated Graphics Controller"
        Monitor         "P95f+-2"
        DefaultDepth    16
        SubSection "Display"
                Depth        16
                Modes           "1920x1440" "1856x1392" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth        24
                Modes           "1920x1440" "1856x1392" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


Xorg log :

[http://marsan.loc.free.fr/Online/Logs/Xorg.0.log](http://marsan.loc.free.fr/Online/Logs/Xorg.0.log)

Thanks a lot for your help ;)

---

### Post by Scorpuk on 2008-03-15
Had no trouble installing the drivers you supplied, but when I run WoW in wine I get an error:

> Your 3D accelerator card is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support.


If i go back to the i810 driver it will run,  but only at 2fps :|


My xorg.conf before failsafe was loaded:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-68
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1368x1026" "1280x1024" "1272x1017" "880x880" "800x600" "720x400" "640x480" "256x256" "152x810"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

