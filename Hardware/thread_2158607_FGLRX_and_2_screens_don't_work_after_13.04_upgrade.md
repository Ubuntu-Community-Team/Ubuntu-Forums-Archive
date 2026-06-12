---
title: "FGLRX and 2 screens don't work after 13.04 upgrade"
date: 2013-06-29
forum: Hardware
---

### Post by jackschmidt on 2013-06-29
I upgraded to 13.04 the other day on my laptop HP Pavilion G4-2123TX (Radeon HD 7600M)  and after fighting with fglrx to get it to load, I managed to get to work using this: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

However, if I plug in my second monitor, I go to the big desktop automatically and the resolution is all broken.  I can "see" my desktop, but the actual painting of the desktop is off.  This didn't happen on 12.10.  I need some help and guidance!

---

### Post by jp734 on 2013-06-30
What do you mean by "I can see desktop but actual painting is off"? If you meant what I think you meant, try adding this to your config file. 

Option  "ColorTilind2D" "Off"

---

### Post by jackschmidt on 2013-06-30
Let me see if I can get a screenshot for you.

EDIT:
The printscreen is showing a correct desktop, but the actual big desktop is misaligned.  The task bar is drawn on the middle and the 2 desktop are off completely.  The problem is similar to what is described here: [http://askubuntu.com/questions/310734/ubuntu-13-04-amd-intel-hybrid-graphics-dual-screen-problems](http://askubuntu.com/questions/310734/ubuntu-13-04-amd-intel-hybrid-graphics-dual-screen-problems) 

When I move the mouse, the desktop is refreshed with the correct alignment for the big desktop, but this only happens for a second, and then the desktop goes back to the broken layout.  This makes the screen flicker really terribly.

---

### Post by jp734 on 2013-07-01
what does your xorg.conf look like and what monitors (model) and resolution are you using for each?

---

### Post by jackschmidt on 2013-07-02
Here is my xorg.conf.  Please note that this is only single screen.  I only hotplug my second monitor as I don't always have it with me.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Here is the resolution I am using: 2390 x 768
My laptop (HP Pavilion G4-2123TX) screen: 1366x768
My Samsung SyncMaster 591s monitor: 1024x768
Both at 60 Hz.

I do not use Mirror Mode.  If I configure mirror mode via settings at 1024x768, the 2 monitors display correctly.  Once I go non-mirror mode, the screen goes insane.

---

### Post by jp734 on 2013-07-02
Two things, for non-mirror mode, you need to specify a virtual screen size:

Virtual 2390x768

Put it under section screen>subsection display.

Then you need xinerama :

Section "severflags"
         Option "xinerama" "on"
EndSection

---

### Post by jackschmidt on 2013-07-02
I tried your suggestion and X wouldn't startup.  I'm assuming I did something wrong.
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
                Virtual 2390x768
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "serverflags"
        Option "xinerama" "on"
EndSection

```

---

### Post by jp734 on 2013-07-02
The easiest way to do this is to run [COLOR=#0000cd]*"aticonfig --initial"*[/COLOR] on terminal.It will make a backup copy of your existing configuration file and create a new one.  If for some odd reason it won't do it for you, you can check the copy of my xorg.conf [here]("http://ubuntuforums.org/showthread.php?t=2156915&page=2"). This is my working setup for 3 monitors using 2 radeon cards. 

I would suggest making sure you have two instances of [COLOR=#0000ff]*Section "Monitor"*[/COLOR] and* [COLOR=#0000ff]Section [/COLOR]*[COLOR=#0000ff]*"**Screen"*[/COLOR] for your second monitor. Also, under *[COLOR=#0000ff]Section "Device"[/COLOR],* you can add the [COLOR=#0000ff]*Option "Monitor...."*[/COLOR]. You will notice on one of my device section, there are options for the two monitors connected on one card.

---

### Post by jackschmidt on 2013-07-03
I have a backup of my xorg.conf so the issue earlier was easily fixed.  My AMD Catalyst Control Center has no Display section, so I cannot seemingly configure the 2nd screen.  I'll have a look at your xorg.conf but it looks to me that you are essentially telling me to write manually my second screen into the xorg.conf, right?

---

### Post by jackschmidt on 2013-07-03
I managed to fiddle around with my xorg.conf but it looks like the end result is just a mirror desktop (and wrong resolutions at that) and randr seems to have been disabled by fglrx (seemingly caused by Xinerama).  Please have a look at my xorg.conf and se if I'm missing something here.

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "Screen1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1366x768"
	Option      "TargetRefresh" "60"
	Option      "Position" "0 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "VGA1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1024x768"
	Option      "TargetRefresh" "60"
	Option      "Positon" "1281 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option "Monitor-LVDS1" "aticonfig-Monitor[0]-0"
	Option "Monitor-VGA1" "VGA1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual 2390 768
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "aticonfig-Device[0]-0"
	Monitor    "VGA1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

```
I also realize that for this xorg.conf to show 2 desktops, I have to boot with my second monitor plugged in, which just creates some very bad mirror desktop.  Hotplugging my 2nd monitor doesn't work.

I have also tried your first suggestion on simply having Xinerama On and Virtual resolution but the end result was very bad. :)

I tried removing Xinerama which re-enabled xrandr but plugging in the second monitor only shows the same issue.

Hope you can help me!

---

### Post by jp734 on 2013-07-03
Two things I noticed. First, the Option "position" for your second monitor can't be "1281 0" because your main monitor is the 1366x768. So technically it should be "1367 0". The other thing, on your "Option "Monitor....", do some research on that. Maybe LVDS1 and VGA1 is not an option (you know what I mean?). That part of my config file was created by AMD catalyst for me so I wouldn't know for sure. I think it will be safe if you change it to "monitor- crt1" and "...-crt2". 

As far as hot plugging, I'll be honest, don't think I can help you there. But will do some research.

---

### Post by jackschmidt on 2013-07-03
You are so right about the position.  I didn't notice that as I was suddenly thinking of a 1280x800 desktop!  I'll go make that change.

As far as the Monitor-xxx settings, that was me guessing it alright.  The problem is, when I run amdcccle, I don't see any display section to configure my displays.  It's always hybrid graphics and some AA options and that's it!

I'll go make some changes.

EDIT:
This guy managed to get the option I want working as far as Monitor-xxx options go.
[http://ubuntuforums.org/showthread.php?t=2115121](http://ubuntuforums.org/showthread.php?t=2115121)

EDIT2:
I modified my xorg.conf

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "Screen1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1366x768"
	Option      "TargetRefresh" "60"
	Option      "Position" "0 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "VGA1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1024x768"
	Option      "TargetRefresh" "60"
	Option      "Positon" "1367 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option "Monitor-LVDS" "aticonfig-Monitor[0]-0"
	Option "Monitor-CRT1" "VGA1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual 2390 768
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "aticonfig-Device[0]-0"
	Monitor    "VGA1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

```

I can only enable the second monitor once I reboot.  Hotplugging doesn't work which seems to be caused by Xinerama.  The second mirror acts as a mirror of my Laptop display screen, so the pointer actually goes off-screen at a certain point on my second monitor.  I will try to remove Xinerama.

EDIT:
I get the same issues as at the start of this thread when Xinerama is disabled.  On 12.10 all of this worked perfectly.  My xorg.conf was just the regular amdconfig --initial and I could hotplug my monitor to fix it.  Moving to 13.04 broke this... I'm wondering if there's a bug with xrandr and fglrx and Xorg 1.13...

---

### Post by jp734 on 2013-07-03
Have you looked at your Xorg.0.log file for clues?

---

### Post by jackschmidt on 2013-07-03
I haven't found anything significant on the Xorg log file.  Do we need Xinerama in there?  It was not needed back in 12.10.

It was also properly parsing the configuration file I had.

```

[    20.192] (==) ServerLayout "aticonfig Layout"
[    20.192] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    20.192] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    20.192] (**) |   |-->Device "aticonfig-Device[0]-0"
[    20.192] (**) |-->Screen "Screen1" (1)
[    20.192] (**) |   |-->Monitor "VGA1"
[    20.192] (**) |   |-->Device "aticonfig-Device[0]-0"

```

I wonder if this is an issue...
```

[    21.062] (WW) fglrx: More than one matching Device section for instances
        (BusID: PCI:1:0:0) found: aticonfig-Device[0]-0

```

Should I be setting primary on LVDS?

Not much in the way of (EE) entries in there.

---

### Post by jp734 on 2013-07-04
As far as I know, if you want the second monitor as an extended desktop, yes you need Xinerama or all you'll get is a cloned screen. 

We need to find out which one drives your first video card output, the second and third (if there is) since you have a hybrid card

execute "lspci" on terminal and check for something like:
  - BusId 1:0:0 Intel
  - BusId 1:0:1 Ati

We've only been playing with fglrx the whole time. Maybe the first output is right with fglrx but the second output is being driven by the intel. We need all the details included on your xorg.conf so we can tell the system *[COLOR="#0000FF"]"the monitor is not hooked up but this is what it will be on this card once it's hooked up"[/COLOR]*

I'm thinking, when you boot it up with everything connected, it detects everything and knows how to configure it. Meaning, your system detects what the Horizontal and Vertical refresh rates range are and the maximum resolution your monitor is capable of. But after it's been booted, it doesn't go through that process of determining your monitors capabilities. So, we will need to work on your Device, Monitor and Screen section of your xorg file

For the monitor section we need to include your monitors Horizontal, Vertical and Resolution as follows. (You need to do some research and find out the refresh rate ranges). 

> Section "Monitor"
	Identifier   "VGA1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1024x768"
[COLOR="#0000FF"]	Option      "TargetRefresh" "60"  COMMENT THIS ONE OUT. JUST ADD # BEFORE OPTION
        HorizSync  30-80
        VertRefresh  50-75[/COLOR]
	Option      "Positon" "1367 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

For your screen resolution add this to your Section Screen > SubSection Display
   > [COLOR="#0000FF"] Modes   1024x768[/COLOR]

For your device section you might need to add a second one if intel is being used and don't forget to specify the busid the card is using.
> Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option	 "Monitor-CRT1" "0-CRT1"
Option	 "Monitor-CRT2" "0-CRT2"
[COLOR="#0000FF"]BusID "PCI:1:0:0"[/COLOR]
EndSection

---

### Post by jackschmidt on 2013-07-04
Okay, so... here's what I got so far.

This is what lspci gives me.
```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

```

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M]

```

I'm going to take a look at the xorg.conf file for your suggestions.

Samsung monitor:
[http://reviews.cnet.com/crt-monitors/samsung-syncmaster-591s-crt/4507-3175_7-31312643.html](http://reviews.cnet.com/crt-monitors/samsung-syncmaster-591s-crt/4507-3175_7-31312643.html)

So, with this, should my settings look like this?
```
HorizSync 55
VertRefresh 120
```

> **jp734 said:**
> 
For your screen resolution add this to your Section Screen > SubSection Display


I presume this is on Screen1?  Just trying to make sure.
```

Section "Screen"
        Identifier "Screen1"
        Device     "aticonfig-Device[0]-0"
        Monitor    "VGA1"
        DefaultDepth     24
        SubSection "Display"
                Modes 1024x768
                Depth     24
        EndSubSection
EndSection

```

---

### Post by jp734 on 2013-07-04
For the screen resolution, YES, that is for your Screen1 (hot plugged monitor) and what you've done is correct. For the refresh rates, I did some searching myself and the range is HorizSync 30-50; VertRefresh 50-120. You can double check from the link below:

[http://www.samsync.com/downloadcenter/products/monitors/crt%20monitors/15/591s/SyncMaster%20591S793S793DF795DF797DF997DF793MB795MB.pdf](http://www.samsync.com/downloadcenter/products/monitors/crt%20monitors/15/591s/SyncMaster%20591S793S793DF795DF797DF997DF793MB795MB.pdf)

Now, as far as your video card, now we know that for your AMD, the [COLOR="#0000FF"]BusID is pci:1:0:0[/COLOR] and [COLOR="#0000FF"]pci:0:2:0[/COLOR] for Intel.

The question now is, the port where you plug in the monitor, is it being driven by Intel or AMD? This plays a big role coz nothing on your xorg.conf file that says we are using the Intel card for this monitor. So I think that would be your next assignment. And as usual, if I get some free time, I will do some research myself coz I like learning this kind of stuff. Never had a hybrid card before and who knows, I or a relative might have one one day. :D And it's fun!

Maybe you can give me a detail on this pc of yours Model, brand, etc.....oops wait, you already mentioned it on your very first post I think.

---

### Post by jackschmidt on 2013-07-04
Yes.  I mentioned it on my first post.  It's an HP Pavilion G4-2123TX and it's a Radeon HD 7670M.

I looked into the xorg log file and saw that it was preloading the intel drivers as well, but I'm not certain as to what it's doing.  I'll post the relevant entries.

```

[    21.745] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    21.746] (--) Chipset Supported AMD Graphics Processor (0x6840) found
[    21.746] (II) fglrx: intel VGA device detected, load intel driver.
[    21.746] (II) LoadModule: "intel"
[    21.759] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.767] (II) Module intel: vendor="X.Org Foundation"
[    21.767]    compiled for 1.13.3, module version = 2.21.6
[    21.767]    Module class: X.Org Video Driver
[    21.767]    ABI class: X.Org Video Driver, version 13.1
[    21.767] (II) AMD Video driver is running on a device belonging to a group t
argeted for this release
[    21.767] (II) AMD Video driver is unsigned
[    21.768] (II) fglrx(0): pEnt->device->identifier=0x7f0313accc80
[    21.768] (II) intel(1): pEnt->device->identifier=(nil)
[    21.768] (EE) Screen 1 deleted because of no matching config section.
[    21.768] (II) UnloadModule: "intel"
[    21.768] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    21.768] (II) fglrx(0): PowerXpress: Discrete GPU is selected.

```

Looks like we hit a dead end here as the intel gpu chip is being deactivated.  I'll try and run the xorg.conf with and without Xinerama (I didn't need to set Xinerama back in 12.10 so you have to forgive my suspicions over this option.)

---

### Post by jp734 on 2013-07-04
Well, we just might be able to activate the intel graphics and set it to use your VGA connection. One more thing to try here and if it doesn't work, then I'm out of idea. So here it is. I'm thinking the reason Screen1 was deleted is because it is for Intel and your xorg.conf says it belongs to AMD. And your intel module is being unloaded because it wasn't mentioned again on your xorg.conf so we are basically telling  the system we don't need it.

So we are going to add another Device Section on your xorg.conf for your Intel graphics and let it use the VGA connection. I edited your configuration file and highlighted the ones I made changes to. Don't forget to make a backup copy of your existing one. Now it's up to you if you still want to try this or not. Or if what I'm thinking even makes sense to you. IT'S ALL UP TO YOU.

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "Screen1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1366x768"
	Option      "TargetRefresh" "60"
	Option      "Position" "0 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "VGA1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option      "PreferredMode" "1024x768"
	[COLOR="#0000FF"]#Option      "TargetRefresh" "60"[/COLOR]  #COMMENTED OUT. DON'T THINK WE NEED IF HORIZSYNC AND VERTREFRESH ARE SPECIFIED
	Option      "Positon" "1367 0"
	Option      "Rotate" "normal"
	Option      "Disable" "false"
	[COLOR="#0000FF"]HorizSync	30-80
	VertRefresh	50-120[/COLOR]
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option 	"Monitor-CRT1" "aticonfig-Monitor[0]-0"
EndSection

[COLOR="#0000FF"]Section "Device"
	Identifier  "Intel_Card"
	Driver      "intel"
	BusID       "PCI:0:2:0"
	Option      "Monitor-CRT1" "VGA1"
EndSection[/COLOR]

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual 2390 768
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	[COLOR="#0000FF"]Device     "Intel_Card"[/COLOR]
	Monitor    "VGA1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

---

### Post by jackschmidt on 2013-07-05
I'm not seeing much sense to this since hybrid graphics chips are supposed to be mutually exclusive.  It's either you use the power saving mode (Intel) or the performance mode (AMD).  It seems rather silly to me that we'd need to use the Intel chip for the VGA port when that wasn't necessary before.  Still, I suppose it's worth a try when I get the time to do it.  Thanks for all your help, by the way.  I appreciate the effort you put into this.

---

### Post by niniendowarrior on 2013-08-01
Maybe this is the cause of the error:
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

---

### Post by niniendowarrior on 2013-10-16
Open source radeon drivers is the only way to go for 2 screens.

---

