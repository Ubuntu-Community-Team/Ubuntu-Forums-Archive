---
title: "Wacom doesn't work well in Ubuntu 11.04"
date: 2011-05-30
forum: Hardware
---

### Post by jsfarney on 2011-05-30
My Wacom Bamboo works in Ubuntu 11.04, but not very well.  It has nowhere near the pressure sensitivity that it has in Windows where I installed the drivers from the cd that came with it.  How can I make this work in Ubuntu the way it works in Windows?  Thanks for the help.

---

### Post by Favux on 2011-05-30
Hi jsfarney,

Which Bamboo model is it?

Enter in a terminal and post the outputs of:
```

lusb

xinput list

xsetwacom list
```

---

### Post by jonathon6017 on 2011-05-30
> **jsfarney said:**
> My Wacom Bamboo works in Ubuntu 11.04, but not very well.  It has nowhere near the pressure sensitivity that it has in Windows where I installed the drivers from the cd that came with it.  How can I make this work in Ubuntu the way it works in Windows?  Thanks for the help.

I kinda have the same issue my tablet (Bamboo Craft, which is pretty much the same as the Fun) works almost perfectly (Pen and touch) it just does not have pressure sensitivity which would be very nice to have.

---

### Post by Favux on 2011-05-30
Hi jonathon6017,

You should have pressure.  Did you configure the extended input devices in Gimp or Inkscape?  If you did post the same diagnostics I asked jsfarney for.

---

### Post by jsfarney on 2011-06-01
It is a Wacom Bamboo CTL - 460.  And there is some pressure sensitivity, but it does not reach the full range of sensitivity that I get in Windows.  Thanks for your help.:KS

---

### Post by Favux on 2011-06-01
Sure.  But we need some diagnostics to look at what's going on.  I'm waiting for the outputs of the above commands so I can give you some further ones to try and look at the issue.

---

### Post by jonathon6017 on 2011-06-01
I played around with the Extended input controls butt all I can seem to do is either disable the pen or just keep it where it is with no pressure sensitivity.

lsusb:
```
jonathon@jonathon-Satellite-L645:~$ lsusb
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 056a:00d2 Wacom Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

xinput list:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Finger pad           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Finger touch         	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Pen eraser           	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Pen stylus           	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNF9055                                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

and finally.....

xsetwacom list:
```
jonathon@jonathon-Satellite-L645:~$ xsetwacom list
Wacom Bamboo Craft Finger pad   	id: 12	type: PAD       
Wacom Bamboo Craft Finger touch 	id: 13	type: TOUCH     
Wacom Bamboo Craft Pen eraser   	id: 14	type: ERASER    
Wacom Bamboo Craft Pen stylus   	id: 15	type: STYLUS  
```

---

### Post by Favux on 2011-06-02
Ok, that's one of the 5 original BambooPT models and there shouldn't be any problems.  The xinput and xsetwacom lists indicate it is on the Wacom X driver.

So what is the output of the following commands entered in a terminal?:
```
xinput list-props "Wacom Bamboo Craft Pen stylus"
```
and
```
xsetwacom get "Wacom Bamboo Craft Pen stylus" PressureCurve
```

---

### Post by jonathon6017 on 2011-06-02
> **Favux said:**
> Ok, that's one of the 5 original BambooPT models and there shouldn't be any problems.  The xinput and xsetwacom lists indicate it is on the Wacom X driver.

So what is the output of the following commands entered in a terminal?:
```
xinput list-props "Wacom Bamboo Craft Pen stylus"
```
and
```
xsetwacom get "Wacom Bamboo Craft Pen stylus" PressureCurve
```

```
jonathon@jonathon-Satellite-L645:~/Downloads$ xinput list-props "Wacom Bamboo Craft Pen stylus"
Device 'Wacom Bamboo Craft Pen stylus':
	Device Enabled (126):	1
	Coordinate Transformation Matrix (128):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (244):	0
	Device Accel Constant Deceleration (245):	1.000000
	Device Accel Adaptive Deceleration (246):	1.000000
	Device Accel Velocity Scaling (247):	10.000000
	Wacom Tablet Area (513):	0, 0, 14720, 9200
	Wacom Rotation (496):	0
	Wacom Pressurecurve (515):	0, 0, 100, 100
	Wacom Serial IDs (497):	210, 0, 2, 0
	Wacom Capacity (500):	-1
	Wacom Pressure Threshold (501):	27
	Wacom Sample and Suppress (502):	2, 4
	Wacom Enable Touch (503):	0
	Wacom Hover Click (518):	0
	Wacom Enable Touch Gesture (504):	0
	Wacom Touch Gesture Parameters (505):	50, 20, 250
	Wacom Tool Type (506):	"STYLUS" (516)
	Wacom Button Actions (507):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (508):	0, 0

```



```
jonathon@jonathon-Satellite-L645:~/Downloads$ xsetwacom get "Wacom Bamboo Craft Pen stylus" PressureCurve
0 0 100 100

```

---

### Post by Favux on 2011-06-02
The PressureCurve is set at the default, which is linear pressure.  What happens if you soften it?
```
xsetwacom set "Wacom Bamboo Craft Pen stylus" PressureCurve 0 10 90 100
```

---

### Post by pSYcl0Ne on 2011-06-03
Hey guys, THANKS! I've found this post very usefull too.

:guitar:

Question: How do I use this to set keybindings for the function keys on the pad?

---

### Post by jonathon6017 on 2011-06-03
AWESOME!!!! It works now thanks!!! But I have the same question, how do you set the key bindings for the buttons?

---

### Post by Favux on 2011-06-03
Hi jonathon6017,

Good!  You might want to play with the graphical PressureCurve demo linked here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve)  to get a better feel.

And of course two manuals are available on your system.  Just enter *man wacom* or *man xsetwacom* in a terminal and they will pop up.


For pSYcl0Ne & jonathon6017,

The manuals above should help.  Since you are both in Natty and have Bamboo Pen & Touches (I think) see the pad button transpositions for Natty described in part V. on the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  There's also sample scripts and other explanations there.  Also see on the Linuw Wacom Project mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  and  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=USB_Tablets_with_Touch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=USB_Tablets_with_Touch)

---

### Post by pSYcl0Ne on 2011-06-03
Thanks heaps Favux, just a quick one.

In Lucid I used to be able to 'hover left click' to hold/scroll web pages in fire fox - but now that's gone. what would that be called so i can put it back?

---

### Post by Favux on 2011-06-03
Well hover should be the xsetwacom parameter TabletPCButton set off, but that should be default for a tablet.  Maybe you're talking about the Firefox extension Grab it All?  Did a little hand appear on the page to grab it and scroll it?  If so that's it.

---

### Post by jsfarney on 2011-06-18
Hey I started this thread a while ago, but I got busy and didn't follow up with it.  Favux, you really seem to know your way around.  Can you please help me with my wacom?  I have entered the commands in the terminal and I got this:

lsusb

'Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 056a:00d4 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

xinput list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Pen eraser                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Pen stylus                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Finger pad                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Finger touch               id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

xsetwacom list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Pen eraser                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Pen stylus                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Finger pad                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen Finger touch               id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
ben@ben:~$ xsetwacom list
Wacom Bamboo Pen Pen eraser         id: 10    type: ERASER    
Wacom Bamboo Pen Pen stylus         id: 11    type: STYLUS    
Wacom Bamboo Pen Finger pad         id: 12    type: PAD       
Wacom Bamboo Pen Finger touch       id: 13    type: TOUCH 

Thanks so much!!!O:)

---

### Post by Favux on 2011-06-18
Hi jsfarney,

Is it still that you feel the pressure isn't as responsive as you'd like?  Have you tried changing the PressureCurve parameter with xsetwacom like jonathon6017 did?

---

### Post by jsfarney on 2011-06-19
Favux, I tried messing around with the things that you told Jonathan to do, but I still didn't get the pressure sensitivity that I wanted.   I really wish I could figure out what's up with this!  Thanks for the help!

---

### Post by Favux on 2011-06-19
From what you've posted the tablet appears to be on the Wacom driver.  What is the issue exactly.  You have pressure, it's just not what you want.  Or you don't seem to have pressure, i.e. if there it is barely noticeable?

---

### Post by jsfarney on 2011-06-20
Well there is a little pressure, but it is barely noticeable.  In Windows, there is all kinds of lights and darks, thick and thin line widths, but when I use my wacom in ubuntu, there is barely any pressure sensitivity even when I use varying pressure.  I just don't understand why in Ubuntu it does not reach the full range of pressures that I get in Windows. :(

---

### Post by Favux on 2011-06-20
If you're able to get full pressure range currently in Windows you've ruled out a hardware problem and the nib being worn down.

What application are you having a problem with?  Or is it more than one?

Since you're on the driver we can look at what the pressure level is set to with the outputs of:
```
xinput list-props "Wacom Bamboo Pen Pen stylus"
and
xsetwacom get "Wacom Bamboo Pen Pen stylus" all
```

---

### Post by theconartist on 2011-06-22
I'm having the same problem with the Bamboo Pen. It's with GIMP, mypaint, krita, everything. Messing with the pressure curves doesn't help. The bottom maybe 1-2 percent of pressure works properly but once u start to press down on it with even a few grams of force it it maxes out. Is there anyway to watch the pressure input data with something like xev?

```
Device 'Wacom Bamboo Pen Pen stylus':
	Device Enabled (144):	1
	Coordinate Transformation Matrix (146):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (260):	0
	Device Accel Constant Deceleration (261):	1.000000
	Device Accel Adaptive Deceleration (262):	1.000000
	Device Accel Velocity Scaling (263):	10.000000
	Wacom Tablet Area (707):	0, 0, 14720, 9200
	Wacom Rotation (708):	0
	Wacom Pressurecurve (709):	0, 10, 90, 100
	Wacom Serial IDs (710):	212, 0, 2, 0
	Wacom Capacity (711):	-1
	Wacom Pressure Threshold (712):	27
	Wacom Sample and Suppress (713):	2, 4
	Wacom Enable Touch (714):	0
	Wacom Hover Click (722):	0
	Wacom Enable Touch Gesture (715):	0
	Wacom Touch Gesture Parameters (716):	50, 20, 250
	Wacom Tool Type (717):	"STYLUS" (720)
	Wacom Button Actions (718):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (719):	0, 0

```


```
Option "Area" "0 0 14720 9200"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Option "PressureCurve" "0 10 90 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "720"
Option "ToolSerial" "0"
Option "TabletID" "212"

```

---

### Post by theconartist on 2011-06-23
This also might be some useful output... is that max what is causing this? Bamboo Pen is just misconfigured in the driver to have max 255 pressure causing it to plateau?

```
$ sudo evtest /dev/input/wacom
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x56a product 0xd4 version 0x106
Input device name: "Wacom Bamboo Pen Pen"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
    Event code 331 (Stylus)
    Event code 332 (Stylus2)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   4901
      Min        0
      Max    14720
      Fuzz       4
    Event code 1 (Y)
      Value   6814
      Min        0
      Max     9200
      Fuzz       4
   [B] Event code 24 (Pressure)
      Value    939
      Min        0
      Max      255
[/B]
```

---

### Post by Favux on 2011-06-23
Hi theconartist,

Now that is interesting.  Tablet PCs have a max. pressure of 256 levels which is what evtest seems to be showing.  So is the Bamboo Pen being conflated with a tablet PC somewhere?  But more basically all pressure levels are suppose to be normalized to 2048 levels in the code, irregardless of the actual pressure levels supported by the device.  But evtest is probably showing the actual situation the Xserver is seeing.  Do you know what pressure levels the Pen is suppose to support?  512 or 1024?

What release of Ubuntu are you using?  Kernel and X server version?  Run *Xorg -version* in a terminal to get that info.  Are you using the default wacom.ko and xf86-input-wacom or did you update them?  If so how?

---

### Post by theconartist on 2011-06-23
The Bamboo Pen is supposed to support 512 levels.

I'm on ubuntu 11.04 with the most recent packages from the repo

X.Org X Server 1.10.1
Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686

---

### Post by Favux on 2011-06-23
OK, Natty.

Right, and the other BambooPTs have 1024.  So the repo is xf86-input-wacom-0.10.11 correct?  The Ubuntu package would be something like xorg-xserver-input-wacom something 0.10.11 something.  You didn't install a PPA or anything?

That'll help figure out if it is something in the kernel (wacom.ko) or the X driver (xf86-input-wacom).


Edit:  Also please check the Xorg.0.log in /var/log.  Search *wacom* in gedit.  There should be a line similar to:
```
[    21.730] (--) Wacom BambooFun 2FG 4x5 Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=100000 resY=100000  tilt=disabled
```
What does your line say?  We're looking at the maxZ.

---

### Post by theconartist on 2011-06-23
```
0.10.11-0ubuntu4 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages)

```

```
[ 54234.772] (--) Wacom Bamboo Pen Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=255 resX=100000 resY=100000  tilt=disabled

```

---

### Post by Favux on 2011-06-23
Yep, there it is maxZ=255 and it should be 511.

Could you compile and install an older version of xf86-input-wacom and see if that fixes the problem?  If it does post the Xorg.0.log line again.  Hopefully the 0.10-10 tar will compile on Natty.  You can follow the instructions in part II. b) of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

If that fixes the problem we'll know it is some commits in the 0.10.10+ tree.  Several look possible to me.  That would be enough information to take to Chris Bagwell to see if he'll fix the problem.  Then you could compile and install 0.11.1 and verify the problem is still present, i.e. it has propagated up since 0.10.11.

---

### Post by theconartist on 2011-06-23
Nope, still doesn't work even from the 10.10 tarball or from the current code from Git
```

[     9.162] (II) Module wacom: vendor="X.Org Foundation"
[     9.162]    compiled for 1.10.1, module version = 0.10.10
```

---

### Post by Favux on 2011-06-23
Alright, so the Xorg.0.log still showed 255 levels for maxZ.

That could mean my guess was wrong and the commit that broke pressure is in an earlier version.  I don't know if your interested in bisecting it further.  It worked in Natty and that was 0.10.8.

The other possibility is it is the kernel.  I just looked at the input-wacom wacom_wac.c and interestingly enough it is saying the Pen has 1024 levels of pressure like the other BambooPTs.  Are you sure about 512?  Anyway let me check on Natty's 2.6.38 kernel's wacom_wac.c.

---

### Post by theconartist on 2011-06-23
The 512 is just what specs say I don't actually know if they are wrong on the specs. And from looking at the xf86-input-wacom sources I think this is going to be the driver problem.
I just hardcoded it to 1023 and its working perfectly for me.

---

### Post by Favux on 2011-06-23
I think I found the problem.  The Wacom site says 512.  Hardcode that in and see if that is OK too please.

Looking at the 2.6.38 kernel's wacom_wac.c it says:
```
static const struct wacom_features wacom_features_0xD4 =
	{ "Wacom Bamboo Pen",     WACOM_PKGLEN_BBFUN,     14720,  9200,  255, 63, BAMBOO_PT };
```
and it should read:
```
static const struct wacom_features wacom_features_0xD4 =
	{ "Wacom Bamboo Pen",     WACOM_PKGLEN_BBFUN,     14720,  9200,  511, 63, BAMBOO_PT };
```
So that's where the 255 is coming from.  I have no idea how that happened.  To fix it it will have to be submitted to linux-input and I guess would show up in the 3.0 kernel.

In the meantime you can use input-wacom since apparently 1023 levels works OK.

---

### Post by theconartist on 2011-06-23
I tried 512 before 1023, it was still cutting it off, so its indeed using it as 1024 levels.

---

### Post by Favux on 2011-06-23
lol  That's interesting too!  I suppose the Wacom site could be wrong.  Why not?

---

### Post by Favux on 2011-06-24
Hi theconartist,

Just an update.  The fix for the Pen will bundled in with a submission by Ping to linux-input shortly.  I believe we're going with 1024 pressure levels.  Ping also found the commit that had the pressure level mistake.  Of course that won't help you now, unless Ubuntu backports the fix in to Natty's kernel.

So for Natty the Bamboo Pen's should use input-wacom for their wacom.ko.  That's described on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  I think Irie's PPA linked there uses a recent input-wacom wacom.ko so you can use the PPA also.

---

### Post by jsfarney on 2011-06-25
Hi, Favux.  I am having problems most notably in Gimp, but I think there is inferioror pressure sensitivity in Synfig Studio and some other programs as well.  These are the outputs of what you told me to put in the terminal:

Device 'Wacom Bamboo Pen Pen stylus':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (273):    0
    Device Accel Constant Deceleration (274):    1.000000
    Device Accel Adaptive Deceleration (275):    1.000000
    Device Accel Velocity Scaling (276):    10.000000
    Wacom Tablet Area (558):    0, 0, 14720, 9200
    Wacom Rotation (559):    0
    Wacom Pressurecurve (560):    0, 0, 100, 100
    Wacom Serial IDs (561):    212, 0, 2, 0
    Wacom Capacity (562):    -1
    Wacom Pressure Threshold (563):    27
    Wacom Sample and Suppress (564):    2, 4
    Wacom Enable Touch (565):    0
    Wacom Hover Click (573):    0
    Wacom Enable Touch Gesture (566):    0
    Wacom Touch Gesture Parameters (567):    50, 20, 250
    Wacom Tool Type (568):    "STYLUS" (571)
    Wacom Button Actions (569):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (570):    0, 0
ben@ben:~$ and
The program 'and' is currently not installed.  You can install it by typing:
sudo apt-get install and
ben@ben:~$ xsetwacom get "Wacom Bamboo Pen Pen stylus" all
Option "Area" "0 0 14720 9200"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Option "PressureCurve" "0 0 100 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "571"
Option "ToolSerial" "0"
Option "TabletID" "212"

Thanks so much for all your help!:)

---

### Post by lendula on 2011-10-06
ani@ubuntu:~$ xinput list-props "Wacom Bamboo Craft Pen stylus"
unable to find device Wacom Bamboo Craft Pen stylus
ani@ubuntu:~$ xsetwacom get "Wacom Bamboo Craft Pen stylus" PressureCurve
Cannot find device 'Wacom Bamboo Craft Pen stylus'.


how do i make my pc detect the wacom tablet ... its bamboo 4x6 and works great on my windows os

---

### Post by Favux on 2011-10-06
Hi lenudla,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?  For example Natty (10.04).

What model of Wacom Bamboo tablet do you have?  Sounds like a Bamboo Craft BambooPT.  The model is on a sticker on the back of the tablet.  Also we want to know the product ID.  That would be in the output of this command in a terminal:
```
lsusb
```
We just need the Wacom line posted.  Also please post the output of the following command:
```
xinput list
```

---

### Post by fatteralbert on 2011-10-08
I borrow this thread a bit. Hope no one minds. 

I'd like to set  the area of the wacom as specified here, [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

It says to put in 

```
Section "InputDevice"         
...              
Option          "TopX"        "100"              
Option          "TopY"        "200"               
Option          "BottomX"     "14000"         
Option          "BottomY"     "6000"         
...     
EndSection
```in the file 

```
/usr/share/X11/xorg.conf.d/50-wacom.conf
```but when I did this my Ubuntu installation stopped working. (No screens were found)

So my question is: how do I set the area?

---

### Post by Favux on 2011-10-08
Hi fatteralbert,

First you should know that Jason is working on adding the KeepShape command back in to the code, although it may be renamed.

You can use either xsetwacom (run time) or static commands to do that.

The problem looks to be your syntax was incorrect.  You only want to add the option:
```

Option          "TopX"        "100"
Option          "TopY"        "200"
Option          "BottomX"     "14000"
Option          "BottomY"     "6000"

```
part of that to the snippet in 50-wacom.conf that is matching your tablet.  Add them below the *Driver "wacom"* line.  Although technically since the 50-wacom.conf is a Distro file you shouldn't make a change to it, see below.

For more information see the mediawiki's HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)  Look at Calibration and Xorg.conf.d in particular.

---

### Post by klatschbatsch on 2011-11-12
Hello, I also got problems with my Wacom Bamboo to work in Ubuntu 11.04. In fact, it doesn't work at all.

I have a Wacom Bamboo Pen CTL-470 (recently purchased) and it doesn't respond in any way (despite the LED on the tablet blinking like it should do, as already tested when using it in Windows).

I also tried the terminal-commands mentioned in this thread to get some information about the device. The results (compared to the ones others have reported) are rather strange.

The command lsusb shows the following:

```
Bus 002 Device 003: ID 056a:00dd Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1690:0741 Askey Computer Corp. [hex] 
Bus 001 Device 003: ID 05c8:030e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So the device is in Bus 002, as Device 003, that seems alright.

xinput list shows the following:

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=7	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                         	id=8	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; FH13FF-238                              	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

I don't know, but maybe the 'Virtual Core XTEST pointer' could be my tablet ( I have no mouse plugged in at the moment).

The command xsetwacom list doesn't show anything. The command itself works, as i get usage information when using 'xsetwacom --help'.

So, my question: What to do?

---

### Post by Favux on 2011-11-12
Hi klatschbatsch,

Welcome to Ubuntu forums!

Your model is new and was just released in October.  So it is not in the drivers yet.  Chris Bagwell has submitted patches for it to the kernel (linux-input) so support for your model should be available with the 3.3 kernel.

In the meantime you'll have to add the support yourself.  The model section near the top of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") has your new model and directs you to appendix 3 at the bottom of the HOW TO.  See also this thread:  [http://ubuntuforums.org/showthread.php?t=1860985](http://ubuntuforums.org/showthread.php?t=1860985)

Hope this helps.

---

### Post by klatschbatsch on 2011-11-13
Hello Favux,

Thank you very much!

I installed the drivers the way it was shown in appendix 3 and it worked instantly! Even the calibration was automatically correctly detected. I tested the functionality with the programs I need and everything worked fine.

Again, thank you. Thank you for your help, and the warm welcome!:)

---

