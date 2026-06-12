---
title: "Sony Bravia 32&quot; uncompatible with Ubuntu?"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by jokakutihuti on 2007-11-03
So I have a desktop computer on which I decided to install Ubuntu on, it has a Radeon X-800 video card, as a screen I use a Sony Bravia 32" LCD HDTV 1366x768 pixels which is connected to the computer through the VGA port on the X800.

Ubuntu shows up but the **problem is that the left part of the desktop is cut off**, beginning from the left side of the "Places" menu in the upper bar. So I'm missing maybe 7-10% of the screen. I've tried it with most of the different resolutions in the System/preferences/Screen resolution menu and I still miss the same section of the desktop. 

The weird thing is that it works just fine with Windows XP, I've even tried hooking my laptop with Vista through the VGA port and it works fine. So any help and advice would be much appreciated, I'm really looking forward to installing all of Ubuntu.

Thanks!
(And hi everyone :))

---

### Post by Nzer24 on 2007-11-03
One way that you might be able to fix this is by adding a custom resolution to xorg.conf so you could display it at that resolution. I could tell you how to do that if you want. 

Does the screen itself have an unique resolution? If so, knowing what it is will be helpful because then you could set the output to match.

---

### Post by jokakutihuti on 2007-11-04
> **Nzer24 said:**
> One way that you might be able to fix this is by adding a custom resolution to xorg.conf so you could display it at that resolution. I could tell you how to do that if you want. 

Yeah, please go ahead. I have no idea what xorg.conf is though, so please be thorough. :)

> **Nzer24 said:**
> 
Does the screen itself have an unique resolution? If so, knowing what it is will be helpful because then you could set the output to match.
There's a sticker on the TV that says 1366x768 pixels.

---

### Post by jokakutihuti on 2007-11-04
Never mind, it seems the problem was just with the TV. I found a submenu in the TV that allowed me to pan the image to the right so now the whole desktop shows up.

Thanks for replying!

---

### Post by WakkiTabakki on 2007-11-04
Hi jokakutihuti
I've got the same setup. I've noticed that if the TV is switched off when X starts up, same thing happens... If the TV is on when Ubuntu starts, it works just fine.

But, you actually got it working with 1366x768? Only works in 1280x768 for me. 
And if I connect the TV via DVI -> HDMI the picture looks awful...

Similar experiences?

Here's my xorg.conf. I use the Serverlayout section to switch screen to use (laptop-only, external monitor as primary or TV as secondary).

```

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

<<< SNIPPED ALL THE INPUT SECTIONS >>>>>


Section "Monitor"
    Identifier     "LaptopPanel"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Samsung"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    VideoRam        524288
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "True"
### 2007-06-10
	Option         "DamageEvents" "True"
	Option         "BackingStore" "True" # Kan ge problem!
	Option         "RenderAccel" "True"
	Option         "UseEDID" "True"
	Option		"UseEDIDDpi"	"False"
	Option          "DPI"           "96 x 96"
EndSection


Section "Screen"
    Identifier     "TV"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LaptopPanel"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0, CRT-0"
    Option         "TwinViewOrientation" "DFP-0 LeftOF CRT-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
    Option         "Metamodes" "DFP-0: 1280x800, CRT-0: 1280x768"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "60"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "LCD"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LaptopPanel"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0"
    Option         "TwinViewOrientation" "DFP-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "Metamodes" "DFP-0: 1280x800"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Monitor"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Samsung"
    DefaultDepth    24

    Option         "UseDisplayDevice" "CRT-0, DFP-0"
    Option         "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "CRT-0, DFP-0"

    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x800 +1280+0"

    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "60"
EndSection


Section "ServerLayout"
    Identifier     "Default Layout"

# Uncomment the screen to use...
    Screen      0  "Monitor" 0 0
#     Screen      0  "TV" 0 0
#    Screen       0 "LCD" 0 0


    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    Option         "Xinerama" "Off"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```


Cheers
/N

---

### Post by jokakutihuti on 2007-11-04
> **WakkiTabakki said:**
> Hi jokakutihuti
I've got the same setup. I've noticed that if the TV is switched off when X starts up, same thing happens... If the TV is on when Ubuntu starts, it works just fine.

But, you actually got it working with 1366x768? Only works in 1280x768 for me. 
And if I connect the TV via DVI -> HDMI the picture looks awful...

Similar experiences?

No I never got it working with 1366x768. I had it working briefly with 1280x768 but then I installed a driver from the "restricted drivers manager" for my video card (X800), when I restarted my screen went blank. I had to drag out my old computer screen just to be able to see anything and turn the resolution to 1024x768 for the Bravia to work, that's what I have now. Anything above 1024x768 and it just goes blank, even though it worked with 1280x768 before the driver install.

Did you change any driver settings after installing Ubuntu?

I haven't noticed any difference with having the TV on/off while booting up.

> **WakkiTabakki said:**
> 
Here's my xorg.conf. I use the Serverlayout section to switch screen to use (laptop-only, external monitor as primary or TV as secondary).

```

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

<<< SNIPPED ALL THE INPUT SECTIONS >>>>>


Section "Monitor"
    Identifier     "LaptopPanel"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Samsung"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    VideoRam        524288
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "True"
### 2007-06-10
	Option         "DamageEvents" "True"
	Option         "BackingStore" "True" # Kan ge problem!
	Option         "RenderAccel" "True"
	Option         "UseEDID" "True"
	Option		"UseEDIDDpi"	"False"
	Option          "DPI"           "96 x 96"
EndSection


Section "Screen"
    Identifier     "TV"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LaptopPanel"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0, CRT-0"
    Option         "TwinViewOrientation" "DFP-0 LeftOF CRT-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
    Option         "Metamodes" "DFP-0: 1280x800, CRT-0: 1280x768"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "60"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "LCD"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LaptopPanel"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0"
    Option         "TwinViewOrientation" "DFP-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "Metamodes" "DFP-0: 1280x800"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Monitor"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Samsung"
    DefaultDepth    24

    Option         "UseDisplayDevice" "CRT-0, DFP-0"
    Option         "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "TwinView" "True"
    Option         "TwinViewXineramaInfoOrder" "CRT-0, DFP-0"

    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x800 +1280+0"

    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "60"
EndSection


Section "ServerLayout"
    Identifier     "Default Layout"

# Uncomment the screen to use...
    Screen      0  "Monitor" 0 0
#     Screen      0  "TV" 0 0
#    Screen       0 "LCD" 0 0


    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    Option         "Xinerama" "Off"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```


Cheers
/N

How does this xorf deal work? (I just installed ubuntu this morning)

Also, what do you mean by "when X starts up"?

---

### Post by hessiess on 2007-11-04
X11 is the grafical user interfece server. gnome/ kde etc are desctop enviroments witch run on top of x.

x starts up when ubuntu switches from the spash screen to the login screen.

it is acsessed with the

sudo gedit /etc/X11/xorg.conf command 

this is the section you are most interested in

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video CardNVIDIA GeForce go 7600"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

just add your disierd resolution in quotes infrunt of all the ones listed.

---

### Post by jokakutihuti on 2007-11-04
> **hessiess said:**
> X11 is the grafical user interfece server. gnome/ kde etc are desctop enviroments witch run on top of x.

x starts up when ubuntu switches from the spash screen to the login screen.

That's what makes it even more weird, the login screen shows up at 1280x768 but after I login it goes back to 1024x768 and if I try to make the resolution higher I just get a "out of range" on my Bravia. Also when I try to watch a movie full screen, I get the same result and I have to restart.

Btw, is this the same X11 that you can find as an application in OSX on macs?
> **hessiess said:**
> 
it is acsessed with the

sudo gedit /etc/X11/xorg.conf command 

this is the section you are most interested in

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video CardNVIDIA GeForce go 7600"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"  "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

just add your disierd resolution in quotes infrunt of all the ones listed.

So I should just copy paste all of that in there?

---

### Post by WakkiTabakki on 2007-11-05
> **jokakutihuti said:**
> 
Btw, is this the same X11 that you can find as an application in OSX on macs?

So I should just copy paste all of that in there?

Yes its the "same" X11, well its heavily modified but its based on XFree86, which Ubuntu also used up until... hmmm... Dapper drake, was it? At that point XFree86 changed its licensing policy making it (ironically) less free and Ubuntu and many others changed to Xorg.


Nope, you should not copy/paste the section, you need to (at least) modify the line
```
Device		"Generic Video CardNVIDIA GeForce go 7600"
```
Look in your xorg.conf and find the 'Device' section. In that section, there is an 'Identifier'-line.
That text should go instead of "Generic Video Card[snip]" in the stuff posted by hessiess...

And (you probably already figured this one out, but...) always keep a working  backup copy of your xorg.conf. It's a b**ch to keep track of what you changed once X goes bust...


And thank for the input on Bravia resolution. Now I know I'm not alone :(...

Cheers
/N

---

### Post by Prefader on 2007-11-05
What I've found works, especially with some DLP TVs (although I'm sure it can work just fine for any 720p-capable set) is to drop in a 720p modeline.  For my friend's DLP, we wanted to output 720p via DVI-HDMI.  To do so, we used  [this wiki (http://www.mythtv.org)]("http://www.mythtv.org/wiki/index.php/Modeline_Database#ATSC_Standard_Modes") to find a 720p modeline that worked for his TV.  The picture is great, although I don't recall if there's some overscan with that modeline (the system is primarily used as a mythtv box, so overscan isn't really a concern there).

There's also some info on the Xorg FAQ regarding building a custom modeline using your xorg logfiles.  I'd look through that as well if none of the modelines above work for you.

---

### Post by jokakutihuti on 2007-11-09
> Section "Device"
	Identifier	"ATI Technologies Inc R420 JJ [Radeon X800SE]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JJ [Radeon X800SE]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection


This is what my xorf.conf looks like right now, how should I change it? Don't shoot the noob. :)

---

### Post by jokakutihuti on 2007-11-12
Bump, please help me. I don't want to go back to Windows.

Could a different release of Linux help?

---

### Post by Prefader on 2007-11-12
Try this:

```
Section "Device"
 Identifier "ATI Technologies Inc R420 JJ [Radeon X800SE]"
 Driver "fglrx"
 Busid "PCI:1:0:0"
 EndSection
 
 Section "Monitor"
 Identifier "Generic Monitor"
     ModeLine "ATSC-720-120p" 148.5 1280 1296 1360 1650 720 722 728 750
 EndSection
 
 Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies Inc R420 JJ [Radeon X800SE]"
 Monitor "Generic Monitor"
 Defaultdepth 24
    SubSection     "Display"
        Depth       24
        Modes       "1280x720"
    EndSubSection
 EndSection
 
 Section "ServerLayout"
 Identifier "Default Layout"
 screen "Default Screen"
 Inputdevice "Generic Keyboard"
 Inputdevice "Configured Mouse"
 
 # Uncomment if you have a wacom tablet
 # InputDevice "stylus" "SendCoreEvents"
 # InputDevice "cursor" "SendCoreEvents"
 # InputDevice "eraser" "SendCoreEvents"
 EndSection
```

The only changes I've made are in the "Monitor" and "Screen" sections.  This should convince your card to output 720p.  To be safe, make a backup copy of your xorg.conf before you make any changes, so that you can revert back to what was at least functional before you made changes.  do this with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

It's interesting to me that your xorg.conf doesn't have any input devices configured, nor any "files" section for fonts, nor any "module" section - can someone tell me, is this unique to gutsy, or is the xorg.conf posted above incomplete?

---

### Post by jokakutihuti on 2007-11-12
> **Prefader said:**
> Try this:

```
Section "Device"
 Identifier "ATI Technologies Inc R420 JJ [Radeon X800SE]"
 Driver "fglrx"
 Busid "PCI:1:0:0"
 EndSection
 
 Section "Monitor"
 Identifier "Generic Monitor"
     ModeLine "ATSC-720-120p" 148.5 1280 1296 1360 1650 720 722 728 750
 EndSection
 
 Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies Inc R420 JJ [Radeon X800SE]"
 Monitor "Generic Monitor"
 Defaultdepth 24
    SubSection     "Display"
        Depth       24
        Modes       "1280x720"
    EndSubSection
 EndSection
 
 Section "ServerLayout"
 Identifier "Default Layout"
 screen "Default Screen"
 Inputdevice "Generic Keyboard"
 Inputdevice "Configured Mouse"
 
 # Uncomment if you have a wacom tablet
 # InputDevice "stylus" "SendCoreEvents"
 # InputDevice "cursor" "SendCoreEvents"
 # InputDevice "eraser" "SendCoreEvents"
 EndSection
```

The only changes I've made are in the "Monitor" and "Screen" sections.  This should convince your card to output 720p.  To be safe, make a backup copy of your xorg.conf before you make any changes, so that you can revert back to what was at least functional before you made changes.  do this with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

It's interesting to me that your xorg.conf doesn't have any input devices configured, nor any "files" section for fonts, nor any "module" section - can someone tell me, is this unique to gutsy, or is the xorg.conf posted above incomplete?

Thanks I'll try it now. I lef some of xorg.conf out as it didn't seem relevant, there's more to it and I remember that at least the mouse and keyboard were configured. I'll post again with the result of this change in a while.

---

### Post by jokakutihuti on 2007-11-12
Ok, that really messed the TV... first I get some weird green-red pattern that can best be described as a poor man's scottish tartar, followed by snow storm in the antnest and finally I end up in some settings menu where I have to choose the screen manually.

Naturally my TV does no appear on the list (which seems quite extensive). The closest thing to mine I can figure is under the Manufacturer "Generic" and Model "LCD Panel 1360x768"

Which gives me the values:
Horizontal Range: 31.5-48.0
Vertical Refresh Rate 56.0 - 65.0

I've tried it with both the "widescreen monitor" box checked, unchecked, all the different resolutions - without any results..

Ideas?

---

### Post by Prefader on 2007-11-12
K, try swapping that modeline for another one.  I just realized that that's supposed to push 120Hz refresh, which is probably very wrong.

Try 
```
ModeLine "ATSC-720-60p"  74.25 1280 1320 1376 1650 720 722 728 750
```
and see if things look any better.

BTW, I'm getting these from [http://www.mythtv.org/wiki/index.php/Modeline_Database#ATSC_Standard_Modes](http://www.mythtv.org/wiki/index.php/Modeline_Database#ATSC_Standard_Modes).  Try whatever you'd like.  Also, try doing a google search for your TV's model number + "modeline", maybe someone else has already figured it out.

---

