---
title: "X Manual Configuration with Radeon - ATI Open Source Driver"
date: 2011-09-26
forum: Hardware
---

### Post by Lamukra on 2011-09-26
[SIZE="4"][COLOR="DarkRed"]This Article is not a copy-paste solution it is actually to learn something!!![/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]WARNING: THIS IS ONLY FOR ATI CARDS, WHICH USE RADEON DRIVER.
OTHER CARD USERS CAN USE THIS ARTICLE ONLY FOR STEPS IN HOW TO CONFIGURE X SERVER, NOT MORE. PROBABLY ALL OR MOST OF THE OPTIONS IN DEVICE SECTION WON'T WORK, BUT PRINCIPLES IN CONFIGURING WILL BE THE SAME(SOME TIPS WILL BE GIVEN DURING THE ARTICLE)[/COLOR][/SIZE]

**[SIZE="1"]Disclaimer: If anyhow you will crash or brake or make you system, hardware, monitor, OS, personal files and everything connected with you personal belongings not suitable for use or even damaged I do not take any responsibility for that. Use this guide for your own sake. I am giving you tips how to faster configure your X server Manually, so you will not spend week on reading, finding and comparing.[/SIZE]**

> Changes and Updates will be posted in this quote

> Attached files:
[LIST]
[*]My xorg.conf - modified to work with any radeon compatible card check yours on [_[COLOR="Red"]RadeonDriver Community Page[/COLOR]_]("https://help.ubuntu.com/community/RadeonDriver")
[/LIST]


[SIZE="2"]You can write me suggestions or any correction tips to this email
[EMAIL="lamukra@gmail.com"]lamukra@gmail.com[/EMAIL][/SIZE]

[SIZE="2"]I hope this Guide will Really Help some of you guys!!![/SIZE]


This article is about Manual setup of X server - what is a main basis for all GUIs (Graphical User Interfaces) in probably all Linux distributions (I don't know them all, but surely for Ubuntu).

[LIST]
[*]In this article you will find configurations for ATI RadeonHD 5650 video card, but it does not mean that it will not help you to setup yours. Principle is the same as it is here.
[/LIST]

[LIST]
[*]In this article I use Open Source Driver - radeon, but this doesn't mean that this info won't help you
[/LIST]

[LIST]
[*]I this article I am using laptop, but it does not mean that you can't use desktop PC
[/LIST]

[LIST]
[*]In this article I use Ubuntu x64 11.04, but this doesn't mean... OK?
[/LIST]

[LIST]
[*]So I hope you got it! :)
[/LIST]
[LIST][*]If this article is about My RadeonHD it doesn't mean that it will not help you to configure yours.[/LIST]


[SIZE="4"]**Introduction**[/SIZE]


[INDENT]I was setting up my X to work with my ATI card for quite a while already. I run through a lot of articles and tutorials, I was testing hell a lot of different combinations in my xorg.conf file and for now have optimal ones that work perfectly for me. Not all Sections are configured in my xorg.conf file, but the main ones that are needed for X proper work are done. Reason why I used xorg.conf is that automatically my Ubuntu did not want to recognize everything correctly, so I started to look up for the solution and seems that I found one, which is working. I hope that it will work for you guys. I spend a lot of time on this and did not find anywhere only one page that explains everything with no missed details. As for a beginner, when I started to read about X and trying to configure, it was frustrating. Small details where missing there and there, and I spend a lot of time for finding them. Now I want to help to other beginners, what might help you and them with setting up their X and graphic cards work properly. I will try to include all the details in here to make it one place for configuration of X server. In the end result, when you will finish reading and configuring, you should end up in here, with exactly same article. Lets Start Then.[/INDENT]


[SIZE="4"]**Know Your System**[/SIZE]


[INDENT]Before you start gather required information


[INDENT][SIZE="3"]System Specifications[/SIZE]

[INDENT]Sony VAIO E series
VPCEB1S1E

_[SIZE="2"]Processor:[/SIZE]_

[INDENT]Intel(R) Core(TM) i5 CPU M 430 @ 2.27GHz
```
cat /proc/cpuinfo
```[/INDENT]

_[SIZE="2"]Video Card:[/SIZE]_

[INDENT]ATI RadeonHD 5650 (Redwood)
```
lspci | grep VGA
```[/INDENT]

_[SIZE="2"]Operating System:[/SIZE]_

[INDENT]Ubuntu x64 11.04 Natty Narwhal
```
cat /etc/lsb-release
```
or
```
cat /etc/issue
```
[/INDENT]
[/INDENT]


[SIZE="3"]Additional Information[/SIZE]
[SIZE="1"]It is useful for general knowledge[/SIZE]


[INDENT]_[SIZE="2"]Kernel Release:[/SIZE]_

[INDENT]2.6.38-11-generic
```
uname -r
```[/INDENT]

_[SIZE="2"]Kernel Version[/SIZE]_

[INDENT]#50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011
```
uname -v
```[/INDENT]

_[SIZE="2"]Check if KMS (Kernel Modesetting) is enabled[/SIZE]_

[INDENT]Command given here will give you number of lines find one that looks similar to this

[[COLOR="Red"]drm[/COLOR]] radeon kernel modesetting enabled.
```
dmesg | grep drm
```
If it is not, then stop reading this article here and go to [_[COLOR="DarkRed"]radeonBuildHowTo#radeon-KMSissues[/COLOR]_]("http://www.x.org/wiki/radeonBuildHowTo#radeon-KMSissues")
It will be quite difficult for a very beginner but you can give it a try.
Normally, you should not get problems with KMS, if you got one then you probably already tried to configure your X or made some mistake in configuration. It will be discussed later[/INDENT][/INDENT][/INDENT][/INDENT]



[SIZE="4"]**Start Configuration in 3 Steps**[/SIZE]

[INDENT][SIZE="2"]1. Start Terminal[/SIZE]
[INDENT]Depending on what configuration you already did, you have different options to start terminal
[LIST=1]
[*]Alt+F2 -> terminal -> Enter
[*]Ctrl+Alt+T
[*]Ctrl+T
[/LIST]
[/INDENT]

[SIZE="2"]2. In terminal run command[/SIZE]

[INDENT]```
sudo X -configure
```

[LIST][*]You might get an error saying something like:

[INDENT]> Fatal server error:
Server is already active for display 0
[INDENT]If this server is no longer running, remove /tmp/.X0-lock
and start again.[/INDENT]

Please consult the The X.Org Foundation support 
at [http://wiki.x.org](http://wiki.x.org) for help.

ddxSigGiveUp: Closing log[/INDENT]

[*]In this case run command:

```
sudo X :1 -configure
```

[*]You will be asked for password

```
[sudo] password for username: 
```[/LIST][/INDENT]
[/INDENT]



[INDENT]After this in your home directory will be created a file with name:

[INDENT]_xorg.conf.new_[/INDENT]

Inside that file will be generated configuration from your X server with necessary Sections.
That configuration will be put into xorg.conf file later

> QUICK TIP

When Speaking about home folder in Linux Distributions(Including Ubuntu), users mean the location of personal directory with all user's personal data. In Ubuntu location is in

_/home/username_ or _~/_

This is two exactly the same paths to home directory

xorg.conf is not present in folders, that are normally referenced in a lot of tutorials, because:
[LIST]
[*][SIZE="2"][COLOR="Red"]On the fresh install xorg.conf have to be created manually!!![/COLOR][/SIZE]
[*][SIZE="2"][COLOR="red"]If you never did X configuration manually you will not find xorg.conf file[/COLOR][/SIZE]
[/LIST]

We are doing it now![/INDENT]



[INDENT][SIZE="2"]3. Create xorg.conf[/SIZE]

[INDENT][LIST]
[*]Copy xorg.conf.new file content into file with name xorg.conf in approproate folder.

> QUICK TIP
Folders that are scanned during system startup for .conf files are:
[SIZE="1"]_Note:_ Last parameter in this list is not always a file name[/SIZE]

/etc/X11/<cmdline>
/usr/etc/X11/<cmdline>
/etc/X11/$XORGCONFIG
/usr/etc/X11/$XORGCONFIG
/etc/X11/xorg.conf
/etc/xorg.conf
/usr/etc/X11/xorg.conf.<hostname>
/usr/etc/X11/xorg.conf
/usr/lib/X11/xorg.conf.<hostname>
/usr/lib/X11/xorg.conf


_[SIZE="2"]We will use /etc/X11[/SIZE]_

There is different ways how you can copy xorg.conf.new into xorg.conf

[LIST=1]
[*]Fastest way is to run terminal command
```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```
[*]Not so fast, but works for beginners

[LIST]
[*]Start Nautilus with root rights

[LIST]
[*]Start terminal and run command
```
sudo nautilus
```
[*]Alt+F2 -> gksudo nautilus -> Enter
[*]
[/LIST]

[*]Go to /home/username
[*]
[*]Copy xorg.conf.new to /etc/X11
[*]
[*]Rename xorg.conf.new to xorg.conf
[/LIST]
[/LIST]


[*]Alternative for creating xorg.conf


[LIST=1]
[*]Open Nautilus with admin rights
[*]
[*]Go to /etc/X11
[*]
[*]Create empty file with name xorg.conf
[*]
[*]Fill in all Sections manually or copy-paste from xorg.conf.new
[/LIST]
[/LIST]
[/INDENT]



Congratulations! Now you have xorg.conf that will be used by X server on startup for setting up your X session with specific parameters.[/INDENT]



**[SIZE="4"]Essentials and Getting Ready[/SIZE]**


[SIZE="3"]_Must read before You Start!!!_[/SIZE]


[[COLOR="Red"]_Xorg.Conf Manual_[/COLOR]]("http://manpages.ubuntu.com/manpages/natty/en/man5/xorg.conf.5.html") - Have to read this! I can't explain everything here from this article. It's huge

[[COLOR="Red"]_ATI - Radeon Open Source Driver Manual_[/COLOR]]("http://manpages.ubuntu.com/manpages/natty/en/man4/radeon.4.html") - you will find essential driver Options for Device Section


[INDENT][SIZE="3"]First Things TO DO.[/SIZE]


[INDENT]When reading material is covered start with erasing all unnecessary information from xorg.conf(for now unnecessary, you will add it back afterwards, but not all of it)
Leave in your xorg.cong file this sections

Section "ServerLayout"

Section "Files"

Section "Module"

Section "Monitor"
The one with Monitor0

Section "Device"
The one with a lot of # signs before Option

> NOTE: Save all Options from Device Section and compare them with Radeon Manual. Not all of the options will be supported by certain Distributions. You will have to test them.

Section "Screen"
The one with Screen0 and Monitor0 in it[/INDENT]


[SIZE="3"]Learn by HEART essential Commands and Places[/SIZE]

[INDENT][SIZE="2"]Places[/SIZE]

[INDENT]Two main places to remember:

```
/var/log
```

Here you will find different logs from system
We will need _Xorg.0.log_ for configurations and checking

```
/etc/X11/xorg.conf
```

Path to your X Configuration file(If you did not choose other)

[/INDENT]
[/INDENT]

[INDENT][SIZE="2"]Commands[/SIZE]

[INDENT][LIST][*]If you want to read entire log in terminal

```
cat /var/log/Xorg.0.log
```

> NOTE: If you want to read normally with text editor, go to given path with nautilus. You might need this command because of not loadable X session due to bad Option in Device Section or syntax error

[*]If you want to grab keywords from log use grep command like this

[INDENT]This will give you error reports

```
cat /var/log/Xorg.0.log | grep EE
```

This will give you warning reports

```
cat /var/log/Xorg.0.log | grep WW
```[/INDENT]

[*]If you want to edit xorg.conf from terminal

```
sudo pico /etc/X11/xorg.conf
```

```
sudo nano /etc/X11/xorg.conf
```

> NOTE: To save press Ctrl+O -> Enter
To exit press Ctrl+X

[*]If you want to copy backup of xorg.conf

```
sudo cp [path to file which to copy] [path where to copy]
```

[INDENT]> Example:
I made a backup copy of xorg.conf to home directory with name xorg.conf.backup

```
sudo cp /home/username/xorg.conf.backup /etc/X11/xorg.conf
```

or

```
sudo cp ~/xorg.conf.backup /etc/X11/xorg.conf
```

[QUOTE]**NB! In root shell use full path to home because ~/ will be root's home directory**

```
cp /home/username/xorg.conf.backup /etc/X11/xorg.conf
```

or if you want you can copy your xorg.conf.new file and start configuring all over again

```
sudo cp /home/username/xorg.conf.new /etc/X11/xorg.conf
```

relatively in root shell

```
cp /home/username/xorg.conf.new /etc/X11/xorg.conf
```[/QUOTE][/LIST]
[/INDENT]
> **NB! If you are in recovery mode(When you boot, you choose kernel to boot with recovery) and choose root shell you do not have to use 'sudo' to enter text editor or execute other commands that need root rights.**[/INDENT][/INDENT]


> **[SIZE="2"]NB! It might happen that you will need to go to root shell in recovery if some option or syntax error made your X server not loadable. Remember This! That is why you have to learn commands and places by heart![/SIZE]**
[/INDENT]

[SIZE="2"]When all set and ready start configuration with Device Section and then as follows:

ServerFlags
Screen and Monitor Sections
ServerLayout Section
InputDevice and InputClass Sections

We will follow them as it is and I will put my snippets of xorg.conf code in next Topic[/SIZE]




[SIZE="4"]**Playing With Sections, Options, Identifiers**[/SIZE]

[SIZE="3"]Essential Key Combinations to Remember[/SIZE]

[INDENT][SIZE="2"]Ctrl+Alt+T - Start Terminal[/SIZE]

[SIZE="2"]Alt+PrtSc+K - X Restart Key Combination[/SIZE]

[SIZE="2"]*_Ctrl+Alt+F2_ - Drop to terminal shell[/SIZE]

[SIZE="2"]*_Ctrl+Alt+F7_ - Go back to GUI[/SIZE]

> NOTE: Last Two Shortcuts is not recommended to use with Unity. When you drop to terminal shell it is not possible to go back to Unity GUI, but works with GNOME 2
[/INDENT]
[INDENT][SIZE="3"]Sections[/SIZE]


[INDENT][LIST][*]Pay Attention on Syntax
[*]DO NOT miss any quotes and close them or you will get not loadable X and loose time with booting to root shell and figuring out a problem.

[*]Each Section should end with EndSection

[*]DOUBLE CHECK!!!

[*]Remember what changes you make. ALWAYS!!!

[*]In order not to loose time remember last change you make. In case if you will crack X you will know what to change back

[*]Change One-by-One and check right away with X Restart Key Combination

[*]In order to get DRI (direct rendering) support this Options should be present in your xorg.conf

```
Section "ServerFlags"
	Option	"AIGLX" "on"
EndSection

Section "Device"
        ...
	Option 		"DRI" "true"
	Option		"AccelMethod" "EXA"
	...
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection
```[/LIST][/INDENT]


[SIZE="3"]Options[/SIZE]


[INDENT][LIST][*]Go through entire Xorg.0.log, it will give you some useful hints and information

[*]Use Radeon Manual, Xorg.Conf Manual and xorg.conf.new file for Options comparing and reference

[*]Enable and Test one by one

[*]if you enabled some Option and want to see if it works check it with X Restart Key Combination and then

```
cat /var/log/Xorg.0.log | grep EE
```
and
```
cat /var/log/Xorg.0.log | grep WW
```
and for example you enabled ColorTiling like:
```
Options "ColorTiling" "true"
```
then check it
```
cat /var/log/Xorg.0.lof | grep ColorTiling
```
or
```
cat /var/log/Xorg.0.lof | grep Color
```
and etc
[/LIST]
[/INDENT]
[/INDENT]


[INDENT][SIZE="3"]My xorg.conf Settings[/SIZE]


[INDENT][SIZE="2"]_Section Device_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "Device"
	Identifier	"ATI Radeon HD 5650"
	Driver		"radeon"
	Option		"EXAVSync" "True"
	Option		"ColorTiling" "on"
	Option		"RenderAccel" "true"
	Option          "EnablePageFlip" "on"
	Option 		"DRI" "true"
	Option		"AccelMethod" "EXA"
	Option		"SwapbuffersWait" "0"
	Option          "Monitor-LVDS" "Left Monitor"
	BusID       	"PCI:1:0:0"
	Option          "Monitor-LVDS" "VaioLCD"
        Option          "Monitor-HDMI-0" "BraviaLCD"
	Option		"IgnoreEDID" "true"
	Screen		0
EndSection
```[/INDENT]


[SIZE="2"]_Section ServerFlags_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "ServerFlags"
	Option	"AIGLX" "on"
EndSection
```
[/INDENT]


[SIZE="2"]_Section Screen and Monitor_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "Screen"
	Identifier "LaptopScreen"
	Device     "ATI Radeon HD 5650"
	Monitor    "VaioLCD"
	DefaultDepth    24
	SubSection "Display"
		Viewport  0 1080
		Depth     24
		Modes	  "1920x1080i" "1366x768" "1280x720" "1152x768" "1024x768" "800x600" "848x480" "720x480" "640x480"
	EndSubSection
EndSection
```

> NOTE: Screen refers to Monitor Section with Identifier VaioLCD and Device Section points to BraviLCD Monitor. This configuration says to X what settings to use for Monitors. I have second screen connected to my Laptop and that is why I have two Monitor Sections

> **NB! Setting Screens and Resolution is a different topic, here will be covered only Card configuration. Find Screen and Monitor Settings further in Thread**

```
Section "Monitor"
	Identifier   "VaioLCD"
	VendorName   "Sony"
	ModelName    "VPC-EB1S1E"
	Option 	     "DPMS"
EndSection

Section "Monitor"
	Identifier   "BraviaLCD"
	VendorName   "Sony"
	ModelName    "BRAVIA KDL-32S3000"
	DisplaySize  1600 900
	Modeline     "1920x1080i" 74.25 1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
	HorizSync    14-48
	VertRefresh  48-62
	Option 	     "DPMS"
EndSection
```[/INDENT]


[SIZE="2"]_Section ServerLayout_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "ServerLayout"
	Identifier     "DualHead"
	Screen      0  "LaptopScreen"
EndSection

```[/INDENT]


[SIZE="2"]_Section Module_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "dbe"
	Load  "glx"
	Load  "type1"
	Load  "freetype"
	Load  "record"
EndSection
```[/INDENT]


[SIZE="2"]_Section DRI_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "DRI"
	Mode 0666
EndSection
```[/INDENT]


[SIZE="2"]_Section Extensions_[/SIZE]

[INDENT]When I went through manuals I ended up with this

```
Section "Extensions"
	Option	"Composite" "Enable"
	Option	"RENDER" "Enable"
	Option	"RANDR" "Enable"
	Option	"DAMAGE" "Enable"
	Option  "GLX" "Enable"
EndSection
```[/INDENT][/INDENT][/INDENT]




[SIZE="4"]**Configuring Screen and Monitor Section**[/SIZE]


> [SIZE="3"]Article is in Progress... Any help and input will be appreciated
[/SIZE]


[SIZE="4"]**Configuring InputDevice Section**[/SIZE]


> [SIZE="3"]I do not have enough knowledge about configuring InputClass Section. An for Me it is Kind a tricky, because I have Synaptics Touchpad and there is a bug report on launchpad about its functionality (Scrolling is not working, gestures problem and multitouch problem). Any help here and input will be appreciated.[/SIZE]

---

### Post by nickmol on 2012-07-30
your one great a guy! you blessed my entire week... been working on this problem for almost 3 weeks now and so now and then in the last 4 months.

Couldn't get my ati card working since 10.04 and you totally rocked it!

/bow /bow /bow

---

### Post by Lamukra on 2012-07-31
> **nickmol said:**
> your one great a guy! you blessed my entire week... been working on this problem for almost 3 weeks now and so now and then in the last 4 months.

Couldn't get my ati card working since 10.04 and you totally rocked it!

/bow /bow /bow


Happy that it helped someone :)

You are very welcome ;)

---

