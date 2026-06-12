---
title: "Fixing low screen resolution for legacy hardware"
date: 2009-11-09
forum: Hardware
---

### Post by ST3ALTHPSYCH0 on 2009-11-09
Last Saturday I undertook to install hardware sensor monitors on my family Ubuntu 9.10 machine which, incidentally, is built from legacy hardware (specs:  Chaintech 7NJL6 mobo, AMD Sempron 2100+, GeForce 4 MX440 GPU, 512 Mb DDR RAM). I was running the proprietary Nvidia driver and max resolution was 800x600 at 60 Hz (monitor supports up to 1600x1200 at 75 Hz). After successfully getting hardware monitoring running I rebooted to discover the wonder of 640x480 resolution!! I was able to reinstate the *high* resolution of 800x600 only by returning to the nv driver.

I tried multiple suggestions of how to edit my xorg.conf file and temporarily enable higher resolutions with xrandr.... all to absolutely no avail (and several instances of console only login). So I continued searching and ran across several entries referring to a GUI from end that could force higher resolutions call displayconfig-gtk.... but alas, the march of progress had obsoleted said config program.

The workaround: Burn a copy of 8.04 LTS and boot to the live desktop. Right click on the main menu, select "edit menus" and enable the "Screens and Graphics" menu item under . Open Screens and Graphics (Applications>other>screens and graphics). Now click on the model of your monitor and choose the type (in my case I chose Generic Monitor 1600x1200). Choose ok. Choose ok again. At this point it will tell you that the changes won't take effect until you reboot, but as we know that will actually cause you to lose all  of your configurations, so don't reboot yet. Copy the xorg.conf file that was just generated for your hardware to a partition on your machine (this file is located in /etc/X11/). Now you may reboot into your harddrive installation of Ubuntu.

After rebooting open a terminal and backup your current xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

```

Next open a root file browser:
Alt+f2
```

gksudo nautilus

```
Navigate to /etc/X11/
Copy the xorg.conf that you generated into the  X11 folder as xorg.conf(if you named it something else you have to make sure that it's xorg.conf now)
reboot

The configuration file generated for my machine had it startign out in pan mode by enabling 2048x1536 virtually. To change this simply open the xorg.conf file as root (sudo gedit /etc/X11/xorg.conf) and change the "virtual" line to your desired resolution, save, and reboot.

If your machine won't accept the new file, I can help you get back to your original configuration, but I don't know enough about editing an xorg.conf file to repair it.

To the Devs (if any happen across this thread), I realize that the screens and graphics broke the xorg.conf file occasionally, but so do n00bs trying to manually edit said file. I would request that this option be reincluded to version 10.04, or extensive testing be done on legacy hardware. The attitude of "buy newer hardware" just doesn't wash when Ubuntu, by design, has requirements and cost that make it an otherwise very effective option for legacy hardware.

---

### Post by Derspankster on 2009-11-10
Sounds plausible. Absolutely nothing pisses me off more about Linux than the CONSTANT video problems people experience. I have not upgraded even once in the past 4 years without having some sort of video issue.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
Like I said in my post.... their GUI interface absolutely can't break more config files than n00bs (like me) who can't generate a working config file from scratch to save their own life. Now more than ever I think they need to add this option back... if someone's equipment is auto-detected they'll never even care that it's available (especially if it's hidden by default like 8.04), but for those who desparately need it, we would search it out.

Let's make this a mini partition. If you've had issues with your video hardware not being configured correctly correctly and could have used the old "Screens and Graphics" to fix this, post up. If there's enough stink, surely they'd put it back in to 10.04... especially since it will be desirable for an LTS to be uber usable to as many as possible.

---

### Post by benjamonk on 2009-12-05
> **ST3ALTHPSYCH0 said:**
> Like I said in my post.... their GUI interface absolutely can't break more config files than n00bs (like me) who can't generate a working config file from scratch to save their own life. Now more than ever I think they need to add this option back... if someone's equipment is auto-detected they'll never even care that it's available (especially if it's hidden by default like 8.04), but for those who desparately need it, we would search it out.

Let's make this a mini partition. If you've had issues with your video hardware not being configured correctly correctly and could have used the old "Screens and Graphics" to fix this, post up. If there's enough stink, surely they'd put it back in to 10.04... especially since it will be desirable for an LTS to be uber usable to as many as possible.

I'm having HUGE problems with this - just installed ubuntu for the first time (9.10) and can't get to use ,ore than 800x600 on a 1024x768 laptop.

IT IS SOOO FRUSTRTING

I have read lots of post, tried a few xrandr commands but still no joy. I don't have an xorg.conf file to edit and i'm not confident in writing my own. 

I've placed posts but had no response - my laptop is not usable so thinking of going back to windows unless someone can help...

---

### Post by bradleypariah on 2009-12-07
@ [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")

I don't want to raise a big stink or anything - I am very grateful for all ubuntu does, just as I'm sure you are as well.  However, I am posting here to add to the thread and say that I am bookmarking this page.

I have had nothing but trouble with video and audio since I began my Linux quest, and I've tried multiple distros of linux on four different machines.  I just think it's worth mentioning.

---

### Post by bradleypariah on 2009-12-07
> **benjamonk said:**
> I don't have an xorg.conf file to edit and i'm not confident in writing my own.

That seems odd... I believe you should have one.  Especially if you've already done a few xrandr commands.  Ubuntu should automatically generate one upon doing so.

In any case - and I'm sorry if this is a stupid question - but did you try [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")'s fix above?  You hadn't mentioned that in your post.  I'm actually going to try that one myself.  I'm downloading 8.04 as we speak to give it a shot.  I thinks it's safe to believe that even if you don't have an xorg.conf file at this point, doing [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")'s fix will create a working one for you.  If it doesn't work, you will be no worse for ware, right?

Don't give up on Linux.  We all know what seedy things Microsoft has done in the past and we see their monetary motivation for what it is.  There is a fix for your problem, I'm sure of it.  In the long run, I think we both know you'll be glad you stuck with us.  :-)

At the very least, dual boot until you're ready to give it the final push.  Cheers.

---

### Post by Phonic_P on 2009-12-07
I followed you're lead up until I discovered that Kubuntu 9.10 has no xorg.conf file. Has anyone got a work around for the above distro????

---

### Post by Chris Edgell on 2009-12-07
It is a very old question for me.  

I'll use the example of the automobile.  I always wondered, if there was a steady march of progress; if there was the attitude "If it ain't broke, don't fix it."  If there was a steady improvement of the car, why would we scrap something working?  Why not just have upgrades that are improvements; each year brought out a car where any bugs were fixed.  I don't mind a change of style, but why are we not building on the known and good, proven and stable?  

If it's free, why would we have to exercise in some kind of planned obsolesence?  With the car there is a matter of the markets, but what are the market issues here?  Sometimes I feel like, as my father used to say, "Jane, this country is built on the middle men.  If it was all free, how could we make a living."

Sometimes I think they don't want to iron the bugs out, to make a flawless system that's free to the consumer, in many ways.  Why don't the developers fix the bugs before moving on to the next competitive car?  It must intertwine with the thinking about the Volkswagon.  You MUST plan obsolesence to keep running in the markets.

In the same way that free from the government puts private enterprise out of business, so constant free food hurts the restaurant business.  But if we put some bugs in our food the restaurants won't get too mad at us.

Have I mixed too many metaphors here?  I think I have gotten far off-topic.  But at the mention of revolution, I did tie my old bandana around my head.

---

### Post by Chris Edgell on 2009-12-07
Sorry I got so carried away (it's been building inside of me with all the problems with sound and resolution.  I started feeling like the catcher, in the rye).

And it all is seeming very off-topic from the title of the thread.  Forgive me.

---

### Post by bradleypariah on 2009-12-08
I think you're kinda right on point.  No one in this post so far is "mad" at ubuntu.  I think we all love the people there.
I think the developers want to know what people are saying about the constant graphics and sound problems.
In the end, these constant problems can only hurt their revenue.
Let's not forget ubuntu/Canonical is a money-making company with employees that need to eat!
They want their operating system to work!  It's the only way to earn money for support, education, swag, and deployments.
I hope people that are experiencing video/audio problems every day with every distro **keep posting here**!  I hope the post gets so big it enables the good folks at Canonical to know what will not only help us, but inevitably help them succeed in making the best operating system they possibly can.
I'm sure they see how many posts per day revolve around these issues.  However, if any of you on-lookers who are having problems end up reading this, **post here**!  No need to get all riled-up.  Just let them know you're out there.  Only good can come from it.  :-)
I think ST3ALTHPSYCH0's purpose in creating this thread was to start a friendly petition... although he refers to it as a revolution, so I won't speak for him.  lol

---

### Post by bradleypariah on 2009-12-08
> **Phonic_P said:**
> I followed you're lead up until I discovered that Kubuntu 9.10 has no xorg.conf file. Has anyone got a work around for the above distro????

[quote=bradleypariah]In any case - and I'm sorry if this is a stupid question - but did you try [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")'s fix above? You hadn't mentioned that in your post. I'm actually going to try that one myself. I'm downloading 8.04 as we speak to give it a shot. **I thinks it's safe to believe that even if you don't have an xorg.conf file at this point, doing [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")'s fix will create a working one for you**.  If it doesn't work, you will be no worse for ware, right?[/quote]

:-)

---

### Post by RickReichert on 2009-12-08
Good thread.  Now I know why my old S3 Virge DX won't put out more than 800x600 under Karmic; no xorg.conf file.  Guess I'll enjoy the nice, big print on my HP vs17 LCD monitor for now.  Too much else to learn about Linux/Ubuntu to work this any more.  Hopefully next release of Ubuntu (Legacy LLama?) will beef up the video controls.

---

### Post by bradleypariah on 2009-12-09
> **bradleypariah said:**
> **I thinks it's safe to believe that even if you don't have an xorg.conf file at this point, doing [ST3ALTHPSYCH0]("http://ubuntuforums.org/member.php?u=927206")'s fix will create a working one for you**.  If it doesn't work, you will be no worse for ware, right?

This is getting ridiculous!  lmao

9.10 does not ***come*** with the file, but 9.10 will **read** the file *if you put it there*.

Please refer to post #1 on how to do this.

---

### Post by ST3ALTHPSYCH0 on 2009-12-09
I haven't been checking back here, thanks for taking up my slack, Bradley. Yes, this is meant as a n00b how-to (post #1)+ petition to return the screens and graphics control.

We will have major problems if they decide to make xorg auto config only, but as long as it will use an xorg.conf file even n00bs can make one with 8.04 LTS. Better d/l the 8.04 .iso before April, b/c it will get harder to find when they replace it with 10.04 (although I will torrent the .iso to anyone who needs it for "obsolete" tools that it included.

---

### Post by SonicSteve on 2009-12-09
+1 for the video problems. 

I'm the IT Head of a private school, we just bought 10 Asus boards p5g41-m that come with the Intel g4100 chipset. In particular they have the GMA x4500 graphics chip. The 3D seems to work OK but it doesn't detect the monitor properly. 800x600 just isn't gonna cut it. 

I'll try the xorg.conf trick tomorrow. Is there a reason why 8.04 live is suggested? Why not 8.10 or 9.04? Didn't they have xorg.conf also?

---

### Post by hobo14 on 2009-12-10
These three lines will create an xorg.conf file for you if you don't have one:

$ **sudo /etc/init.d/gdm stop**

$ **sudo Xorg -configure**

$ **sudo /etc/init.d/gdm start**


Make sure you write down lines 2 and 3 BEFORE you execute line 1.

Line 1 will stop X - you will be in a black screen with nothing but a shell.

Line 2 generates the file (but only if X has been shut down)

Line 3 starts X again.


You will have to login after lines 1 and 3.

EDIT: actually, to be accurate, line 2 creates the file as ~/xorg.conf.new

you will then need to move it to it's intended location:

$ **sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**

---

### Post by ST3ALTHPSYCH0 on 2009-12-10
Sonicsteve- yes, they all have an xorg.conf (even 9.10, but it just tells the machine to use the detected hardware), but only 8.04 has the "screens and graphics" tool to build a complete config file in one shot.

---

### Post by SonicSteve on 2009-12-10
OK I think I'll have to a bit creative. 8.04 doesn't know what an Intel gma x4500 is. Does anyone know what part of the xorg.conf file is responsible for telling Ubuntu to ignore it?
EDIT
It seems that ubuntu only ignores the xorg.conf it doesn't exist. As long as it's there, Ubuntu is told to read and use it. so I have a xorg file now, with a defined monitor but I still have no options beyond 800x600.

I can't believe more people haven't come across this problem, there seems to be very little about fixing it. 
Here is my xorg.conf, I tried to make is simple with a CRT 1024x768 

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
    Load  "dbe"
    Load  "dri"
    Load  "extmod"
    Load  "glx"
    Load  "dri2"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier    "Screen0"
    Vendorname    "Generic CRT Display"
    Modelname    "Monitor 1024x768"
    Horizsync    31.5-61.0
    Vertrefresh    50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    Gamma    1.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "4 Series Chipset Integrated Graphics Controller"
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

---

### Post by bradleypariah on 2009-12-10
> **SonicSteve said:**
> I can't believe more people haven't come across this problem, there seems to be very little about fixing it. 

*Viva* La *Revolución...*

---

### Post by BuntuFreak on 2009-12-10
I have an old PIII PC with Intel Desktop Board and Onboard Graphics. I was able to run 1280 x 1024 with Gutsy 8.10. As soon as I upgraded to 9.04 my resolution was stuck at 800x600. I upgraded to 9.10, but no difference.

My xorg.conf got regenerated and trashed, i.e no backup was created, so I don't know what I had. What I have in xorg.conf is just a few lines. Even if I delete xorg.conf I get the same results, i.e. 800x600. So having it or not having it makes no difference.

So I followed your instructions using 8.04 CD and generated a xorg.conf file. On the Virtual line it gave me a wide screen resolution (why????) So I tried 1024 x 768 and 800 x 600. Neither worked. I have reverted back to old xorg.conf (or none, makes no difference as I said). Would you be able to help me if I pasted my xorg.conf contents here?

I'm already bald and searching for hairs to pull.

Thanks in advance.

---

### Post by ST3ALTHPSYCH0 on 2009-12-10
I can take a look. I make no promises..... my sig isn't a joke. I've only been using Ubuntu since Oct, and windows 7 is my primary OS. 
I did forget to mention that I was defaulted to a virtual screen of 2048x1536, but I did get that fixed. 
Please post between [noparse] ```
    
``` [/noparse] tags, and let me know what you want your resolution and refresh rate to default to.

---

### Post by BuntuFreak on 2009-12-10
I tried both ways. First your way using 8.04 Install CD, etc. and then with X -configure. I will provide both here.

xorg.conf using 8.04 CD tool (GIVES BLACK SCREEN)
-------------------------------------------------
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 815"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
	Option		"XaaNoPixmapCache"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	800	600
		Modes		"800x600@60"	"832x624@75"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@75"	"1280x960@60"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection



xorg.conf using X -configure (Can get in but still stuck at 800x600)
--------------------------------------------------------------------
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
	Load  "dri"
	Load  "dri2"
	Load  "glx"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
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

#Section "Monitor"
#	Identifier   "Monitor0"
#	VendorName   "Monitor Vendor"
#	ModelName    "Monitor Model"
#EndSection
Section "Monitor"
	Identifier	"Screen0"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
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
	BoardName   "82815 Chipset Graphics Controller (CGC)"
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


Thanks much.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
I'm still trying to get through my comparison of the two files, but my first question is concerning the one you made with 8.04. If you wanted a resolution of 1280x1024, why did you have it configure for a 1024x768 monitor?
Also, I still need  to know the resolution you want and the specs of your monitor (or even the model number and I'll hunt them down for you).


Alright, no promises, but I've edited your files into one and told the xserver to default to a 1280x960x60Hz refresh rate (that seems flickery to me, but it's the highest refresh that both files offfered... and they virtually matched, BTW)

Try this:
Open a terminal
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
That will back your current configuration up (good habit to get into, b/c when you get this working you'll always want to have that file backed up).
```

sudo gedit /etc/X11/xorg.conf

```
Delete the entire contents. Cut and paste the following in:
```

Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "dri"
Load "dri2"
Load "glx"
Load "record"
Load "dbe"
Load "extmod"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

#Section "Monitor"
# Identifier "Monitor0"
# VendorName "Monitor Vendor"
# ModelName "Monitor Model"
#EndSection
Section "Monitor"
Identifier "Screen0"
Vendorname "Generic CRT Display"
Modelname "Monitor 1024x768"
Horizsync 31.5-61.0
Vertrefresh 50-75
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
Gamma 1.0
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option "NoAccel" # [<bool>]
#Option "SWcursor" # [<bool>]
#Option "ColorKey" # <i>
#Option "CacheLines" # <i>
#Option "Dac6Bit" # [<bool>]
#Option "DRI" # [<bool>]
#Option "NoDDC" # [<bool>]
#Option "ShowCache" # [<bool>]
#Option "XvMCSurfaces" # <i>
#Option "PageFlip" # [<bool>]
Identifier "Card0"
Driver "intel"
VendorName "Intel Corporation"
BoardName "82815 Chipset Graphics Controller (CGC)"
BusID "PCI:0:2:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1280 960
Modes "1280x960@60" "1024x768@60" "800x600@60" "832x624@75" "800x600@75" "1024x768@75" "800x600@72" "1024x768@70" "800x600@56" "640x480@75"  "640x480@72" "640x480@60"
EndSubSection
EndSection

```
Save and reboot. If it works, let me know.... if not, get me your monitor info, and we'll try again!

---

### Post by alzie on 2009-12-11
First, Thank You ST3ALTHPSYCH0, I finally got my native 1280x1024 resolution back.

I'm running an older 1.86 MHz Athlon with an Nvidia GeForce 6200 video card, dual booting with Wubi so my situation is slightly different.

Basically when I went into 8.10 I followed your directions to generate the xorg.conf using "screens and graphics" and copied that xorg.conf file to a thumb drive.

When I used the replacement xorg.conf I ended up with an "out of frequency" error.  I opened up a terminal (ctrl+alt+F1) and managed to get my old xorg.conf back.

In order to get it to work in 9.10 I had to remove my Nvidia hardware drivers then I cut and pasted the entire 8.10 xorg.conf into 9.10's file.

Reboot and I have 1400x1050 resolution.  It was a bit disorienting. Next I used "Display" to change resolution, reinstalled the Nvidia hardware drivers and now I'm good to go.

I agree with other posters that we need to get "Screens and Graphics" back for people like me who need help to set up their monitor and video properly.

Thanks again for the solution,  I'm certain you'll help more people than you know.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
I spent 3 days after my resolution went to 640x480 with the proprietary drivers... I'm just trying to reduce the duration of others' headaches!

I just submitted the idea to reinclude this tool on Brainstorm. If it moves to the popular ideas I'll post the link so that we can vote it up!!

---

### Post by BuntuFreak on 2009-12-11
Reply to Post # 23.

My monitor is capable of running 1600 x 1200. It is NOT a widescreen monitor. I have run it with Ubuntu in 1280 x 1024. I mentioned that just for historical purposes to inform you that it did run. But it was not easy on the eyes, so I had settled for 1024 x 768.

So my goal is run it in 1024 x 768 and now I'm stuck at 800 x 600. 

My monitor is an IBM CRT. "G73" on front. When I use the 8.04 tool I could select "IBM" and "G70", but no "G73". So I followed the advice to select "Generic".

Not sure exactly what additional information I can provide that can help. Am at work now, but will give the xorg.conf you created for me a shot this evening. I will check this thread again in case you have any changes for me.

Regardless, thanks much for taking the time. 

Best.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
Let's start with seeing if that works. If it does we can add the 1024x768x75 option (your monitor supports a refresh of 75 Hz, and that will be easier on the eyes.
If it works at 1024x768x60, then post the output of:
```

cvt 1024 768 75

```

This will give me the information I need to add said resolution to the xorg.conf file.

---

### Post by BuntuFreak on 2009-12-11
Here's my report

The following line made the display not fit on my 4:3 monitor since the resolution specified is 16:9

Virtual 1280 960

So I changed the following line to 

Virtual 1024 768

I again got the display but no upper lower tool bars. Approximately an inch down and right from the Left Top corner I saw two ZEROs (WTF?). Again I see the background picture but no upper and lower toolbars. So I changed the line to the following

Virtual 800 600

Now I have my display back. Which means I'm back to square one. One thing silly - the display looks a little better. I don't know why, but it just looks....the word is "clearer".

Anything else we can try?

Thanks.

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
I'm tapped, sorry. I do want to point out that 1280x960 is 4:3 (1280x720 is 16:9), however I don't know enough to help you any further. It took me 3 LONG days to get my resolution woes sorted out. I'm sorry that I can't help further, but I'm sure that if you keep searching you can get the resolution you want. If I stumble across any information that I think would be pertinent to you, I'll forward it.

---

### Post by kjtruitt on 2009-12-21
This worked right away on my Gateway Solo 9500 with Ubuntu 9.10.  It's
a complete xorg.conf file that wasn't there but I created it with this
content:

```
Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility M4 AGP"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M4 AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


```

This was posted by ayuffa in this forum.  May not help anybody with another machine, but it sure did free me from 800 x 600.

---

### Post by MarkX on 2009-12-24
> **SonicSteve said:**
> ...

I can't believe more people haven't come across this problem, there seems to be very little about fixing it.  


I come accross this problem all the time with hardware that isn't even "legacy" and each time it takes me days to fix it. 
It's one of the things that puts me off Linux: The inability of it's writers to fix the most basic flaws, while adding unnecessary fancy nonsense that I don't need. Another one is getting permanent permission to look at my own damn files.

Anyway... I have a DGM 1680x1050 monitor and an Nvidia (Asus) FX5200 connected by DVI. Can't get the right resolution. 
Managed to get to the xorg.config file but on the modlines there are numbers after the resolutions and I don't know what numbers to put after the new 1680x1050 line I want to add. How do I find out please???

---

### Post by MarkX on 2009-12-25
Anyone know how the new DVI (instead of VGA) cable interface works? Doesn't it tell the computer what the monitor is supposed to be capable of?
Doesn't that mean one must somehow disable the automatic detection stuff first?

---

### Post by MarkX on 2009-12-26
Was up late for hours last night and still no joy. Did the Xrandr stuff with no effect and edited the xconfig file. Both now have my preferred resolution in it but it still doesn't show in either the nvidia nor the display options. I suspect it might be something to do with the naming of the screen/monitor???

EDIT: Well I managed to get the right resolution but not in a way that I find acceptable. Now having problems making it stick as the default, even though it's in the menus.

I won't even bother to explain how because as far as resolutions are concerned Ubuntu, Xorg and the Nvidia drivers are simply not fit for purpose. The only way this will get repaired is if people complain to high heaven about it and sadly they won't if they are helped to sort their problems the hard way. Sorry.

---

### Post by ST3ALTHPSYCH0 on 2009-12-27
To answer your question about the modelines, you generate that with the cvt command. for instance, if you want 1680x1050@60 Hz you'd enter:
```

cvt 1680 1050 60

```
Then it will give you the modeline you'll need to add to your xorg.conf.

I realize that we need better resolution configuration tools (the giveaway was when I installed windows 98 on my quad boot machine, and it offered resolutions that took days of tinkering to get with any current Ubuntu, save Ultimate Edition), but I'm not willing to suffer with 640x480 graphics waiting for a better interface.

---

### Post by bradleypariah on 2009-12-28
> **MarkX said:**
> Anyone know how the new DVI (instead of VGA) cable interface works? Doesn't it tell the computer what the monitor is supposed to be capable of?

Yes.  "In theory".  However, it doesn't work in Ubuntu.  :-(

My standard 16x9 widescreen's only available resolutions via DVI were 600x800 and (gulp) ***1920x540***???  WTF?!

> **MarkX said:**
> 
Doesn't that mean one must somehow disable the automatic detection stuff first?

"Somehow" is the keyword in that question, my friend.
:confused:

---

### Post by MarkX on 2009-12-29
Thanks, used cvt.
Maybe I'm paranoid but this Ubuntu resolution problem hasn't improved but got worse. It's almost like some doen't WANT it to be fixed. It must be putting off a lot of potential new users.

---

### Post by ST3ALTHPSYCH0 on 2009-12-29
I don't know about "doesn't want it to be fixed" but I do know that I've seen several posts where someone couldn't get their resolution sorted out and gave up on Ubuntu. My biggest problem came after booting a live USB of Ultimate edition and it started with a resolution of 1154x864 on the same hardware mentioned in my OP. Why can it start so high on generic drivers and vanilla Ubuntu can't?

---

### Post by jessejazza on 2009-12-31
> **ST3ALTHPSYCH0 said:**
> Like I said in my post.... their GUI interface absolutely can't break more config files than n00bs (like me) who can't generate a working config file from scratch to save their own life. Now more than ever I think they need to add this option back... if someone's equipment is auto-detected they'll never even care that it's available (especially if it's hidden by default like 8.04), but for those who desparately need it, we would search it out.

Let's make this a mini partition. If you've had issues with your video hardware not being configured correctly correctly and could have used the old "Screens and Graphics" to fix this, post up. If there's enough stink, surely they'd put it back in to 10.04... especially since it will be desirable for an LTS to be uber usable to as many as possible.

I tried to upgrade to 8.10 when it came out and found problems trying to change a CRT to 1024 x 768... went back to 8.04 [and good old Screens & Graphics]... tried each ubuntu release since and tried to read up info. When i tried editing xorg.conf that part was fine but couldn't get it to work - blank screen or whatever. I think i've installed 9.10 about 6 times now. Even copied the 8.04 Xorg.conf file over... and all sorts.

I'm an intelligent individual but i have to say i do wonder what all the other folk are doing to reliably change resolution - i must be the ubuntu n00b of the world!!!!!

I'm afraid i gave up. Tried SimplyMepis and haven't looked back - but i liked gnome and have much to thank ubuntu for and don't want to change. Until they can provide a simple graphics selection for those who aren't so hardware knowledgeable... i can't regard ubuntu as the #1 distro.

If 10.4 has display selection sorted fine... but Fedora has, Centos and Suse seem ok. I started with ubuntu and want to continue using ubuntu!

---

### Post by jessejazza on 2009-12-31
Another way of putting it!

If i've got to spend 3-4 days fiddling around to sort out a v.basic matter - what has it cost me... a fortune in lost time when i need to be doing work.

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
I put Ultimate Edition on my Ubuntu only machine two days ago, and I think I'll stick with that from here on.... even though it requires 3 times the HD space to install.

---

### Post by jessejazza on 2010-01-02
Ultimate... i've not tried that. Does it set screen resolution differently then. As i wanted to use gnome i tried Mint... but tat was the same as ubuntu.

---

### Post by ST3ALTHPSYCH0 on 2010-01-02
It seems to offer a lot more resolution chooses by default, and didn't revert me to 640x480 after I installed the Nvidia driver, but I noticed yesterday when I fired up a 9.10 Live CD that it gave me 1152x864 in the live environment, but has defaulted to 800x600 each of the three times I've installed it on that machine.

---

### Post by jessejazza on 2010-01-06
> **MarkX said:**
> Was up late for hours last night and still no joy. Did the Xrandr stuff with no effect and edited the xconfig file. Both now have my preferred resolution in it but it still doesn't show in either the nvidia nor the display options. I suspect it might be something to do with the naming of the screen/monitor???

EDIT: Well I managed to get the right resolution but not in a way that I find acceptable. Now having problems making it stick as the default, even though it's in the menus.

I won't even bother to explain how because as far as resolutions are concerned Ubuntu, Xorg and the Nvidia drivers are simply not fit for purpose. The only way this will get repaired is if people complain to high heaven about it and sadly they won't if they are helped to sort their problems the hard way. Sorry.

I've used ubuntu for 3 yrs now... i have much to thank ubuntu for in being my first linux distro. 'Screens & Graphics' was simple and fit for purpose. It seems gnome have replaced it and it's only ubuntu that haven't sorted it. Fedora is fine, mepis and PCLos as well... just a shame about one or two other things with those distros.

I've given up with ubuntu now and have installed Centos. Behind on fancy stuff maybe but WHAT MATTERS works fine. When it comes to donating cash to development i'm happy to donate to distros which are thoroughly tested and feel no obligation towards those that don't.

---

### Post by onefr on 2010-01-15
I am also having problems with sound and resolution.  So frustrating! ](*,)

---

### Post by hakan69 on 2010-01-18
My Gigabyte motherboard with Intel G41/X4500 gave me no more than 800x600. Following the advice in this link:
[http://www.linuxreaders.com/2009/11/04/](http://www.linuxreaders.com/2009/11/04/)
I now enjoy 1920x1080!

Regards/Hakan

---

### Post by bearsomg on 2010-01-20
After dealing with the same issue on my computer, I finally solved it. Check out my post [http://ubuntuforums.org/showthread.php?t=1251234](http://ubuntuforums.org/showthread.php?t=1251234)


Look at my last post on the first page.

---

