---
title: "Guide: Ubuntu on Gateway T-6836"
date: 2008-08-05
forum: Hardware
---

### Post by kaoskorruption on 2008-08-05
[COLOR="Red"]This guide is now out of date. Please read the 9.04 guide [here]("http://ubuntuforums.org/showthread.php?p=7574382#post7574382")![/COLOR]

**Updated August 30, 2008 1:00 AM EST**

I created this guide after getting Ubuntu 8.04 (Hardy Heron) configured with my laptop so that other people can benefit from my experiences. If you have any questions or suggestions let me know! [FONT=Courier New]Note that instructions in this font indicate that you are supposed to run the command in the terminal (Applications -> Accessories -> Terminal).[/FONT]
[IMG]http://content.gateway.com/www.gateway.com/media/products/large/t6836.jpg[/IMG]
Also, I want to say that if you are looking at buying a Gateway T-Series, it is a very nice laptop and I highly recommend it. I have not come across any major problems and for the price it is a steal. I am planning on using this for home and school use for my senior year in high school and hopefully all through college as it is a lightweight computer too.

ENJOY!

/etc/X11/[SIZE=5]xorg.conf[/SIZE]:
[COLOR=Red]**Warning:**[/COLOR]** Back up your xorg.conf before editing.**
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection


Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "vesa"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1024x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Virtual 2624 1200
        Depth    24
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "800x600@56"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "vesa"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    1
EndSection
Section "device" # 
    Identifier    "device2"
    Boardname    "VESA driver (generic)"
    Busid        "PCI:0:2:1"
    Driver        "vesa"
    Screen    0
EndSection
Section "ServerFlags"
EndSection
```[SIZE=5]Screen[/SIZE] (LCD Screen; For VGA Output Scroll Down)
_[COLOR=Red]Problem:[/COLOR] The Gnome desktop is not widescreen causing the panel to not stretch all the way to the right corners._
**Related Topic:** [http://ubuntuforums.org/showthread.php?t=879373](http://ubuntuforums.org/showthread.php?t=879373)
1. [FONT=Courier New]sudo gedit /etc/X11/xinit/xinitrc[/FONT]
2. Add the following line to the bottom, save, and close:
```
xrandr --output TV --off
```3. [FONT=Courier New]sudo gedit /etc/gdm/Init/Default[/FONT]
4. Add the following line (same as above) before the line that says "gdmwhich () {":
```
xrandr --output TV --off
```_[COLOR=Red]How-To:[/COLOR] Automatically dim the screen when on battery power to make the battery last longer._
1. [FONT=Courier New]sudo gedit /etc/acpi/battery.d/99-backlight.sh[/FONT]
2. Insert the following code:
```
#!/bin/bash
if on_ac_power; then
setpci -s 00:02.0 F4.B=FF
else
setpci -s 00:02.0 F4.B=B2
fi
```3. [FONT=Courier New]sudo chmod +x /etc/acpi/battery.d/99-backlight.sh[/FONT]
4. [FONT=Courier New]sudo cp /etc/acpi/battery.d/99-backlight.sh /etc/acpi/ac.d[/FONT]
5. [FONT=Courier New]sudo cp /etc/acpi/battery.d/99-backlight.sh /etc/acpi/start.d[/FONT]
6. [FONT=Courier New]sudo cp /etc/acpi/battery.d/99-backlight.sh /etc/acpi/resume.d[/FONT]

_[COLOR=Red]Problem:[/COLOR] Function Keys Do Not Adjust Brightness_
There is no good fix for this, so for now the only solution is to use Wine and install a Windows brightness control.
1) Install Wine (Applications -> Add/Remove, Search for Wine)
2) Download [Gamma Panel]("http://www.donationcoders.com/stars/files/gapa.zip") from [http://www.donationcoders.com/stars/index.php?show=gapa](http://www.donationcoders.com/stars/index.php?show=gapa).
3) Unzip.
4) Put gapa.exe into your home folder. You can use it by running it from here, but the more desirable thing to do is to put a shortcut in the System Preferences menu. Continue to step 6 to do this.
5) Right click on "System" and click "Edit Menus."
6) Go down to the Preferences section and click "Add Item." Name it something like "Adjust Brightness," pick an icon, and use "wine /home/*user*gapa.exe". This will add an easily accessible icon in your System Preferences menu.
_Note:_ I recommend making two color profiles - one with default brightness for adapter use and one with reduced brightness for battery use.


[SIZE=5]VGA Output[/SIZE]
VGA Output is the port on the back left of the machine where you can plug in a regular computer monitor.
_[COLOR=Red]How-To:[/COLOR] Enable VGA output._
**Related Link:** [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things)
1) Make sure cables are plugged in tight and monitor is turned on.
2) Make sure the input source for the monitor (if it is a TV) is set to the computer.
3) [FONT=Courier New]xrandr --output VGA --auto[/FONT]
**Notes:** This will work if you just want the picture to show, but if you want to get complicated, I recommend using Grandr. To get this, go to System -> Synaptic Package Manager and searching for "grandr." Once installed, open the terminal and type in "grandr." Then hit enter and it should open. I would also recommend placing a shortcut in the Administration menu. To do this:
1) Right-click on System, and click "Edit Menus."
2) Scroll down Administration on the left and expand it.
3) Click on "New Item."
4) Name it something like "Display Configuration."
5) Enter "grandr" for the command.
6) Click OK. Now in the future you can access this nifty tool through the Administration menu.
[b]Notes:[b] I also really recommend reading the above related link about xrandr as it is VERY informative and useful if you plan on using an external display such as a projector, monitor, or TV.

[SIZE=5]DVD Playback[/SIZE]
_[COLOR=Red]How-To:[/COLOR] Get the codecs necessary for DVD playback._
**Related Topic:** [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
**Related Link:** [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support)
1) [FONT=Courier New]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list[/FONT]
2) [FONT=Courier New]wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update[/FONT]
3) [FONT=Courier New]sudo apt-get remove gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar[/FONT]
4) [FONT=Courier New]sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc[/FONT]
_Note:_ If you use Compiz-Fusion, please see the next problem and solution or your DVD will not play.

_[COLOR=Red]Problem:[/COLOR] Playing a DVD causes a blank and/or blue screen._
**Related Links:** [http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html), [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_for_Video_Playback_Problem_in_Compiz-Fusion](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_for_Video_Playback_Problem_in_Compiz-Fusion)
This problem is caused by using Compiz-Fusion while trying to play a DVD.
1) Go to Settings -> Preferences.
2) Expand Video section -> Output modules.
3) Check the "Advanced options" box. (Bottom right)
4) Set "video output module" to "X11 video output" in dropdown menu.
Now try playing a DVD and it should work.

[SIZE=5]iPod Support[/SIZE]
_[COLOR=Red]How-To:[/COLOR]Update your iPod from Ubuntu using Floola._
**Related Links:**[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)
1) Download Floola [here]("http://www.floola.com/download/click.php?action=go&to=lin").
2) Extract the Floola-linux folder /etc and rename it to just "floola."
3) [FONT=Courier New]cd /etc/floola[/FONT]
4) [FONT=Courier New]chmod +x Floola[/FONT]
5) [FONT=Courier New]sudo apt-get install libstdc++5[/FONT]
6) [FONT=Courier New]./Floola[/FONT]
7) If you get errors, check [here]("http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting") in the linux section for fixes.
8)  Make sure you put at least one song on the iPod from iTunes on a Windows or Mac machine before you connect the iPod, otherwise this will not work.
9) Once you plug in the iPod, Floola will ask you what generation your iPod is. Select the correct generation.
10) Some generations require a FWID code. To get this, use [FONT=Courier New]sudo lsusb -v | grep -i Serial[/FONT].
The FWID is the code that is exactly 16 characters long.
11) You can now add media to your iPod by going to Item -> Add in Floola.
12) If you want to create a link to Floola, right click on the Applications menu and click "Edit Menus."
13) Select the "Sound & Video" section, and click "Add Item."
14) Name it Floola and put "/etc/floola/Floola" for the command. Give it an icon and a description and enjoy!

[SIZE=5]Disk Usage Analyzer[/SIZE]
_[COLOR=Red]Problem:[/COLOR] The Disk Usage Analyzer (Applications -> Accessories -> Disk Usage Analyzer detects the wrong amount of dataspace on the harddrive._
**Related Topic:**[http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)
In the Disk Usage Analyzer, go to Edit -> Preferences and uncheck everything that is not your hard drive (where the mount point is "/" or the device is "/dev/sda*" - particularly gvfs-fuse-daemon which duplicates the hard drive causing the detected hard drive space to double.

[SIZE=5]Webcam[/SIZE]
_[COLOR=Red]How-To:[/COLOR] Use webcam._ Camorama does not work. Get the application called "Cheese" instead. Go to Applications -> Add/Remove and search for "Cheese" or "webcam" and install the Cheese application.
_Note:_ If you search for "webcam" in the Add/Remove Applications window and install the "Camera Monitor" application, you will always know for sure when the webcam is turned on.

[SIZE=5]Things That Are Not Yet Working:[/SIZE]
-Some graphical applications have "always on top attributes." For example, in Google Earth, the graphical map part of the screen is always on top, even if there is another window there. I think this has to do with Compiz-Fusion, but I'm not sure.
-The Music Player and DVD keyboard shortcuts do not work.
-Function keys for adjusting the brightness do not work.
-Some videos, such as some Apple movie trailers, do not play in Firefox. Where the movie should be playing, there is simply the message "Mplayer movie is playing..." and they LIE!
-4L (Lightscribe Program) Does not detect Labelflash drive.

**Thanks to the following contributers for helping solve many problems:**
-timothy.malone
-DanTMWTMP
-Genecks

---

### Post by timothy.malone on 2008-08-06
I was about to post a similar guide but you've fixed more than I have. I will add that to fix the resolution bug at the login screen you can add the following command to the beginning of /etc/X11/xinit/xinitrc:

xrandr --output TV --off

This is the only fix for the resolution problem that has worked for me. For some reason when I try the xorg.conf method X starts with the Vesa driver instead of the Intel one.

Also, I had to force pm-utils to unload all my usb modules before going to sleep. If I didn't do this it would only sleep and resume one time. After that one time it would act like it was about to sleep but khubd would refuse to freeze and I'd be thrown back to my desktop. You do that by adding the following file: /etc/pm/config.d/modules with the following contents:

SUSPEND_MODULES="uvcvideo sg usb_storage libusual ehci_hcd uhci_hcd usbcore"

It works for me at least and it took a long time to track that down. If only the brightness controls would work like they're supposed to.

Tim

---

### Post by kaoskorruption on 2008-08-06
I just realized something. At one point after I had put that line in my xorg I reconfig'ed my xorg.conf file and the new file did not have that line anymore. Yet somehow my screen has still been fine.

I havn't messed with sleeping/hibernating much yet.

Also, do sudo displayconfig-gtk and tell me what settings you have. Here are mine:

[[IMG]http://img410.imageshack.us/img410/788/screenshotscreenandgrapzb6.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshotscreenandgrapzb6.png)[[IMG]http://img177.imageshack.us/img177/5072/screenshotscreenandgrapvu0.th.png[/IMG]](http://img177.imageshack.us/my.php?image=screenshotscreenandgrapvu0.png)

Changing any settings with this tool for me never seem to work. Either I mess everything up terribly or the changes just don't get applied. Whenever I checked it before today both of the drivers said VESA, and I never thought to change them until you brought it up. I changed them both to Intel 965 which caused the computer to not even recognize the graphics card at all and go into low-graphics mode. I had to reset my xorg.conf to what it had been before and now this is what it shows.

---

### Post by timothy.malone on 2008-08-07
my settings are similar except for one difference. My driver is listed as 'none' on the first graphics adapter. I know that isn't correct because I have DRI working. Every time I tried to use that tool to change things I ended up with a 640x480 screen. I liked the old days when you had a full Xorg.conf file (or XF86Config file) that listed all of the settings instead of this autodetection stuff they do now. :) At least with that, you knew what was going on without digging in the logs. You could also, when you got things just right, upload your config file and share it with others.  I guess this is easier, when things go right. But when things go wrong it gets pretty complicated.

That gamma app works wonders. It even shows up in the systray so I can have it startup with my session.

Tim

---

### Post by kaoskorruption on 2008-08-08
Yeah, so I think it's offical: displayconfig-gui sucks. I actually meant to post my xorg.conf before, thanks for reminding me. Would you mind posting yours, I'm curious if it is the same or not, mostly when it comes to the driver part.

Oh yeah BTW. Bluetooth. If you go to change the Bios settings at the Gateway bootup screen there is some bluetooth option, and there is also a bluetooth key (Fn + F6), yet there does not appear to be any bluetooth. What is this all about do you think?

---

### Post by timothy.malone on 2008-08-10
The bluetooth thing is weird and I saw it mentioned in some reviews. Maybe it's just for controlling a bluetooth add-on or something.

My Xorg.conf is pretty bare. I haven't played with it at all because every time I touch it Xorg defaults to the vesa driver.
```

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

what sort of glxgears numbers do you get? With compositing on I get around 1200 frames per second. I'm wondering if that is a bit low or not. My last computer had a very slow Savage graphics card. 1200 is high compared to that turtle.

---

### Post by Ecologger on 2008-08-12
This guide was helpful but I still cannot keep my resolution settings static. Every time I restart, my Xorg does not include the 1280x800@60 resolution and I have to add it and ctrl alt backspace and then use displayconfig to change resolution.

---

### Post by jake_won on 2008-08-19
Awesome guide dude!
I bought the exact same laptop from BestBuy last week but couldn't get the screen resolution to work. I can't wait to try it out when I get home. 

BTW, did you get the webcam to work as well?

---

### Post by jake_won on 2008-08-19
Okay... here is what I did...

Take a look at below...

my xorg.conf
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
```

my output of xrandr
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0
```

my /etc/X11/xinit/xinitrc
```
#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
```

Without changing anything, when I run **xrandr --output TV --off** it works out and I can get the 1280x800 resolution. It's just that even when I add the line **xrandr --output TV --off**, the display is still weird everytime I restart. Is there any way to make this permanent? I even tried adding **Options "Ignore" "true"** under the Monitor section of xorg.conf but still nothing...

I hope someone can help me...

---

### Post by simuflite on 2008-08-21
Hi all,

I just got my T-6836 and I'm glad I found this thread. I hope the login screen issue gets solved. I'll be watching this thread for sure.

Thanks for putting this together for everyone.

---

### Post by kaoskorruption on 2008-08-21
Yeah the webcam is working with Cheese. For some reason Camorama didn't work for me, but neither did I spend much time messing with it. I havn't yet tried doing webcam messenging. I'll add that to the guide.

Also, I recommend getting the Camera Monitor application so that you always know for sure when the camera is on and off so that you never get recorded when you don't expect it.

---

### Post by kaoskorruption on 2008-08-21
For everyone that can't get the resolution changes to stay static (ecologger, jake_won):

Did you try adding the command to /etc/X11/xinit/xinitrc? If not, do that like it says in the guide. If not, I'm not really sure what to say, maybe try using the xorg.conf that I have posted and see if it works with that.

timothy.malone - I'm not really sure what compositing is or how to turn it on, but here are my glxgears results:
```
4000 frames in 5.0 seconds = 799.957 FPS
4966 frames in 5.0 seconds = 993.198 FPS
5406 frames in 5.0 seconds = 1081.179 FPS
5453 frames in 5.0 seconds = 1090.573 FPS
5207 frames in 5.0 seconds = 1041.231 FPS
5176 frames in 5.0 seconds = 1035.068 FPS

```

---

### Post by odwyerda on 2008-08-21
Fixed the problem wasnt paying attention to what I was doing.
Apologies

---

### Post by odwyerda on 2008-08-21
.

---

### Post by odwyerda on 2008-08-21
Is it possible to write a programme that would excute the 
```
 xrandr --output TV --off 
```
at startup to bypass the editing of the xorg/conf file with 
```
 Option "Ignore" "true" 
```
which just messed up my graphic card drivers at start up.
I have zero programming knowledge on how to do this but its an idea.


Dave

---

### Post by simuflite on 2008-08-21
> **odwyerda said:**
> I had the same problem. After copying the OP's xorg.conf file to mine, I fixed it by going into System > Preferences > Screen Resolution. There is a monitor called 'Unknown' - select it, then turn if 'OFF' on the Resolution drop-down menu. As soon as you apply the changed the screen should automatically correct to 1280x800.

Perhaps this errant 'Unknown' display is the source of the login screen issue?

---

### Post by DanTMWTMP on 2008-08-22
Hello.  This tutorial has been VERY helpful in setting up my T-6311 running Fedora Core 9.


I'd like to add one thing as well.  I solved the login/boot screen resolution issue.  It's just a variation of what's been already mentioned, but this method worked for me.  

In xorg.conf, add the following:

```
Section "Monitor"
        Identifier  "TVOut"
        Option      "Disable" "true"
EndSection
```

Under the "device section, add the following:
```
Option      "monitor-TV" "TVOutput"
```

Example (excerpt from my xorg.conf):
```

Section "Device"
        Identifier  "Videocard0"
        Driver      "intel"
#       BoardName   "vesa"
        BusID       "PCI:0:2:0"
        Screen      0
        Option      "monitor-TV" "TVOutput"
EndSection

```

Man, hehe, the wine solution for the gamma controls is pretty creative.  I would've never thought of that.  Then again, I'm pretty slow haha.

---

### Post by DanTMWTMP on 2008-08-22
Anyone get suspend to work?  Everytime mine suspends, my backlight gets killed until I reboot.

---

### Post by kaoskorruption on 2008-08-23
DanTMWTMP,

Two questions: What graphics card do you have and could you post your entire xorg.conf? I couldn't get the login screen to work with the changes that you made, but then again, it could be that you are using Fedora Core.

---

### Post by timothy.malone on 2008-08-24
Ok, I posted the wrong fix for the GDM screen. :) If you want to fix the login screen without messing with xorg.conf (adding the Option ignore thingy never worked for me), do the following:
sudo gedit /etc/gdm/Init/Default

then paste this right before the line that says "gdmwhich () {":
xrandr --output TV --off

do the same for the file /etc/gdm/PreSession/Default. I haven't tested to see which one is actually necessary (my guess is that only one is) but I haven't done any trial and error to figure it out because it works for me now. The xinitrc fix may or may not be needed after this, but I'd do it anyway since it doesn't hurt anything. :) Again, some trial and error would quickly sort that out.

Also, if you want your backlight dimming to work without using Wine you can install xbacklight: sudo apt-get install xbacklight

It runs from the command line but only while in X. You can do this for instance: xbacklight -set 65
Don't go all the way down though. That caused my backlight to stay off until I rebooted. I tried making acpid run this command when I unplug the power cord but this only works if I manually restart acpid after booting up. I'm going to do some more investigating and if I figure it out I'll post the solution here.

---

### Post by simuflite on 2008-08-24
Did anyone try installing the Linux drivers for the Intel 3100 chipset?

They're avail here: [http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2568&DwnldID=13653&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2568&DwnldID=13653&lang=eng)

---

### Post by kaoskorruption on 2008-08-25
timothy.malone:

The first one worked! You don't need the second one. Much appreciated. I will add this to the guide.

Also, for the brightness - maybe you could apply your idea to these fixes:
[http://ubuntuforums.org/showthread.php?t=673946](http://ubuntuforums.org/showthread.php?t=673946)
[http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness+keyboard](http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness+keyboard)

I've tried both fixes and neither works, BUT, I think that what those fixes do are execute a command when you press Fn + whatever the brightness adjustment keys are, and if you could add your command to that script, maybe it would work.

If that doesn't work, maybe we could try just having it get dimmer when you unplug it and brighter when you plug it back in?

---

### Post by ilario73 on 2008-08-26
The tricks work also for Packard Bell EasyNote laptop.
THanks, Ilario

---

### Post by simynona on 2008-08-27
Thanks! This was really helpful.

---

### Post by timothy.malone on 2008-08-28
kaoskorruption:

I tried to add the xbacklight fix to one of the fixes you mentioned, and it sorta works. One, I still have to restart the acpid process every time I boot my laptop before it will work. Two, instead of doing one step at a time, it does like five steps (so, when I decreae the brightness it goes to like 28%). It also puts an error in syslog about the script exiting incorrectly. I'll into it a bit more later. I'm also going to see if the problem is in the DSDT table (essentially this is how Linux interacts with ACPI in the BIOS).

Tim

---

### Post by timothy.malone on 2008-08-28
Ok, so this is probably not the prefered way to do this, but it works for me. I take no responsibility for any ill effects it may have.
I found out that you can directly control the brightness through the program setpci.
so, to make the backlight turn itself down when you go on battery power, you can do the following.
create (as root or with sudo) a file called /etc/acpi/battery.d/99-backlight.sh
with the following content:
#!/bin/bash
if on_ac_power; then
   setpci -s 00:02.0 F4.B=FF
else
 setpci -s 00:02.0 F4.B=B2
fi


make the file executable: sudo chmod +x /etc/acpi/battery.d/99-backlight.sh
then copy it to the following locations (with sudo):
/etc/acpi/ac.d
/etc/acpi/start.d
/etc/acpi/resume.d

This works for me and it also works in the command line (xbacklight only worked in X).
The next exercise is to make the brightness keys use that command. I'll work on that next.

Tim

---

### Post by Genecks on 2008-08-29
Nice guide so far. You have saved me some time.
I'll give some tips, but first some comments.

I think the most important thing is to tell people to make a backup of /etc/X11/xorg.conf.
That's always the biggy when playing with xorg.conf files.

Secondly, the guide could use an time stamp (recently updated stamp) in bold at the top for when you have updated and notes about the update. Things became unsure as I continued reading, making me wonder if your first post was continually updated.

> This works for me and it also works in the command line (xbacklight only worked in X).
The next exercise is to make the brightness keys use that command. I'll work on that next.

Tim

Tip: xbindkeys

"xbindkeys is a program that allows you to launch shell commands with your keyboard or your mouse under X Window. It links commands to keys or mouse buttons, using a configuration file. It's independant of the window manager and can capture all keyboard keys (ex: Power, Wake...). "

> Version 1.8.0 : Enable a full access to the xbindkeys internal from the guile scheme configuration file. ***_A grabbed key can start a shell command_*** or run a scheme function. This enable to do more powerfull things inside xbindkeys whitout the need of an external shell script (like double click, timed double click or keys combinations).
 - [http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

[COLOR="Red"]Newer versions should do this, too.[/COLOR]

I suggest you find a way to bind them to Fn and the keys with the sun on them.
It shouldn't be too difficult.
I'd help more, but I'm busy doing my own thing at the moment.

**[COLOR="Red"][SIZE="4"]Comment about Webcam:[/SIZE][/COLOR]**

It seems to work on certain kernel versions.
Something around 2.6.26-1.
Maybe newer than that, too.
I can verify it works on that kernel version, at least with Debian Sid.
I don't know about earlier kernels. A person would have to do research for that.
Cheese is the program I used with the kernel to view if the webcam was working.
The webcam does work


[SIZE="5"]XServer[/SIZE]

Advice to readers about resolution changes:

You may want to increase the font size of things you are reading. I suggest font size 12 if you plan on using 1200x800 resolution. I believe the ability to change fontsize is found in Menu>System>Appearance>Fonts for newer Ubuntu/Debian versions.

Some commands that readers may find useful:
> 
# pkill gdm
# reboot
# gdm

Tips:

1) Try editing all the files before you go back into the X server.
2) You probably don't want to edit and replace the WHOLE xorg.conf file. If you do and end up short, then you might want to edit only certain parts. Figure out which parts to replace. You might replace other parts later in the future, but this part of my post is covering the resolution issue.
3) I found after editing everything and entering gdm again (before a reboot) that the resolution was whack and I couldn't turn it down. I decided to reboot, and it helped me get access to the menu to change the resolution. If anyone knows the command that accesses the resolution program, it would be nice if he/she could list it.

[SIZE="4"]xorg.conf[/SIZE]

The ones in bold I left alone. The bold were named as something similar. But I decided I wanted xorg to see them as it had originally listed them. You could try replacing the whole xorg file, but I didn't.

> 
[B]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection[/B]

[B]Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection[/B]


[B]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection[/B]

[B]Section "Device"
	Identifier	"Configured Video Device"[/B]
	Boardname	"vesa"
**	Busid		"PCI:0:2:0"**
	Driver		"intel"
	Screen	0
**EndSection**

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

[B]Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"[/B]
	Defaultdepth	24
	SubSection "Display"
		Virtual 2624 1200
		Depth	24
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "ServerFlags"
EndSection

[SIZE="6"]Sound card[/SIZE]
The sound card works in kernel version 2.6.25-2 with Debian Lenny. I can listen to Motley Crue and other kinds of music. I apologize that I'm using Debian, but I hope maybe Ubuntu's kernel version and program updates correlate to what Debian Lenny is doing at the moment. I know the sound card does work, and can work without a bunch of trial-and-error stuff that most of the web suggests. It's just about updating to newer stuff. Updating and finding the newer thing.

---

### Post by Ecologger on 2008-09-07
Success!

---

### Post by kaoskorruption on 2008-09-08
Haha is this success in the brightness keyboard shortcuts? If so, want to share? =D

---

### Post by Ecologger on 2008-09-08
It was in making my resolution permenant so I don't have to keep my laptop in perpetual hibernation.

---

### Post by CryoMax on 2008-09-29
The tutorial worked spot-on for me; I bought the Gateway T-6836 specifically because of the walkthrough.  I had only two glitches in my install so far:

One, the Memorex black media CD-Rs I'd bought 8 years ago (I bought a big spindle, and, well, I just don't burn all that much) didn't work.  This was an issue even before I installed Ubuntu, but since I discovered this when I was trying to get the machine to boot off the Ubuntu install CD (and the disk I burned worked fine in my other computers), I thought I'd mention it so other people might not pull their hair out trying to figure out why their burned CD isn't working.  :)

The other thing I noticed, which may have nothing to do with this, is that I tested the DVD player after following the directions, and the movie did, in fact, play -- but when I moved the slider to advance forward/back, it never seemed to start playing again, regardless of whether I hit play/pause or whatnot.  The scene changed when I advanced, so it was definitely reading the DVD, but it would just sit on that frame.

Otherwise, so far, this has been a really lovely installation process.  :)

---

### Post by Genecks on 2008-10-05
[SIZE="7"](October 5th, 2008)[/SIZE]

**[SIZE="5"]ON THE MATTERS OF THE SOUND CARD:[/SIZE]**

Sound does work, but some more recent kernels might cause problems.
I know I make **this post about Debian**, but maybe someone can apply it to Ubuntu. I figure every bit helps.

- Short version:

Kernel 2.6.26-1-686-bigmem causes problems with sound

- Might not allow headphone jack to work
- Works with internal speaker

Kernel 2.6.25-2-686 seems to work with sound but there may be exceptions.

(as of October 5th, 2008)

- Continues to allow usage of headphones
- works with internal speakers

- long version:

At the moment, I'm using Debian Sid.
Originally, I had Debian Lenny installed.
And with Lenny there was a 2.6.25-2-686 kernel installed.
I eventually upgraded to Debian Sid via apt-get dist-upgrade.

That brought in the more recent 2.6.26-1 kernel.
The sound was working for a while with that kernel, but it seems an alsaconf upgrade disabled things from working.

I decided to re-enable the older kernel in /boot/grub/menu.lst. I re-enabled the 2.6.25-2-686 kernel. It continues to work with the soundcard. I'm saying that Sid combined with the leftover kernel (2.6.25-2) from lenny, works well with the sound card.

With the 2.6.25-2-686 kernel, the internal speakers and headphone port continue to work.

**[SIZE="5"]ON THE MATTERS OF THE WIRELESS DEVICE:[/SIZE]**

The wireless device in Debian uses iwl3945.
$ modprobe iwl3945

As of last week, a newer version of iwl3945 was released for Debian Sid. It appears to work well with the laptop. I have not encountered problems so far.

> **CryoMax said:**
> The tutorial worked spot-on for me; I bought the Gateway T-6836 specifically because of the walkthrough.  I had only two glitches in my install so far:

One, the Memorex black media CD-Rs I'd bought 8 years ago (I bought a big spindle, and, well, I just don't burn all that much) didn't work.  This was an issue even before I installed Ubuntu, but since I discovered this when I was trying to get the machine to boot off the Ubuntu install CD (and the disk I burned worked fine in my other computers), I thought I'd mention it so other people might not pull their hair out trying to figure out why their burned CD isn't working.  :)

The other thing I noticed, which may have nothing to do with this, is that I tested the DVD player after following the directions, and the movie did, in fact, play -- but when I moved the slider to advance forward/back, it never seemed to start playing again, regardless of whether I hit play/pause or whatnot.  The scene changed when I advanced, so it was definitely reading the DVD, but it would just sit on that frame.

Otherwise, so far, this has been a really lovely installation process.  :)

The problems with CD-Rs haven't been talked about much. I know what you mean, though. I think it has to do with Linux developers and open-source programmers not thinking too much about CD-Rs that are that old. I tried using some old CD-Rs and CD-RWs a few months ago. They didn't burn. I believe it may have been due to whatever controls the drive interface. I think it's a hardware and software issue. For instance, I had an ounce more of success if I tried to burn something at a really low speed. I decided to get a really old CD-burner. That had maybe a 20% success rate with burning. I think this is a more serious issue and needs to come to the concern of developers. Then again, the things aren't too expensive.

I think issue might have to do with recent hardware. Perhaps some standards changed. I mean, I was surprised when I saw that CDs were like 700MB and not 650MB anymore.

I'm not really sure what the issue is. My knowledge of engineering and computer science isn't that far yet.

But if you are *unable to read* the data, then I'm sure developers would get uppity and get right to work on such a problem.

---

### Post by nycazncarguy on 2008-10-06
Hey, i just wanted to say that this guide helped me alot.  It also helped me understand how the whole thing works under the hood as well.  I greatly appreciate it.

Also, I just wanted to say that the media shortcut keys actually do work in the default movie player ubuntu comes with.  I got so used to pressing those buttons with winamp back in windows, and i happened to be playing a song real quick in the movie player program.  I pressed stop, and it actually stopped!  I was like wait.....this is linux though.. I pressed play, and it started to play.  So maybe we can figure out how to get it working from there?  I dunno, I thought maybe that would be just a start and would be good to know.  That's all the contribution I can make so far...sorry!

---

### Post by mettlewk on 2008-10-22
Hi,
:oops: trivial problem.

---

### Post by mettlewk on 2008-10-23
------

---

### Post by mettlewk on 2008-10-23
-----

---

### Post by kaoskorruption on 2008-10-30
Has anybody tried updating to 8.10?

---

### Post by nycazncarguy on 2008-10-30
I did.  However, I did a fresh install, so I dunno if there will be any differences between that and upgrading...I do know that some settings stay if you upgrade and i wouldnt know if that would affect 8.10.  From the fresh install perspective, however, i must say one thing.  THE SCREEN ISSUE HAS BEEN FIXED.  Intrepid automatically  detects the correct resolution for this laptop now.  My biggest gripe: The media keys used to work somewhat, and at least the mute/unmute button did.  Now, it doesn't work at all.  You can adjust the volume with the touch-sensitive thing, but the mute button doesnt work now either.  Just beautiful...
Also, Intrepid detects the brightness setting from the function keys.  You see the icon with the bar going up and down.  However, nothing actually happens...
Aside from that, I must say, I'm very happy with this.  IMO, it runs faster, feels more stable, and has some nice integration with certain software.  For example, pidgin status is now also attached to the (what used to be more like) the shutdown options button on the top-left and the status can be changed from there.

I'm not sure if this has to do with the servers, but when I download new software, it's slow as hell.  Also, when I made changes to my synaptic manager for installing awn, synaptic wasn't able to download from the repositories I added.  It couldnt even get the list from it's own repositories.  Again, dunno if that has to do with servers, but yeah.

After all that, I do not see any reason as to why not to upgrade.  Go ahead! =)
I'll be making edits as I find out more.

EDIT
compiz seems to lag now.  Trying to see if there's some settings I can change around to make it more smooth again.  Anybody got any clue?

EDIT 2
headphone jack doesn't work.

---

### Post by Ecologger on 2008-11-06
yeah, I did fresh install with 8.10 and my headphone jack does not work any more. I had previously upgraded from 8.04 to 8.10 and it did work, but then I had to do a fresh install. I have fiddled around with modprobe a bit but I could not find any option for the STAC9205 audio chip that would work.

---

### Post by kaoskorruption on 2008-11-08
That's a bit scary. Headphone jack is very important. I'll have to hold off on upgrading until this gets sorted out.

---

### Post by Ecologger on 2008-11-08
Compiling alsa drivers from the latest source 1.0.18 also does not solve the problem.

---

### Post by Ecologger on 2008-11-10
any help out there? I mean I know a lot of people are having similar problems and I have tried a lot to fix it to no avail.

---

### Post by nycazncarguy on 2008-11-11
I have no clue what I did.  Maybe it was a simple restart, maybe it was something I downloaded from the given programs list, I'm not sure.  I do know, however, that my headphone jack works without a problem now.  I guess I can try to figure out what I did to make it work, but that probably won't happen till next week at earliest.

---

### Post by odwyerda on 2008-11-13
Intrepid messed up my machine and I had to do a reinstall of Hardy.
Problems were:
Network manager refused to work on my college network, only could use it in college so I was net less :(
Places-> to any folder didn't work had to make a shortcut on desktop to go anywhere.
Hibernate went ga ga would restart only sometimes.


In the end I had to get rid of it maybe just due to my laptop and other software I had installed but thats my experience.


Dave

---

### Post by Ecologger on 2008-11-13
nycazncarguy: Keep me apprised, I really want a solution to the problem. 
odwyerda: Did you do a fresh install of intrepid or did you upgrade?

---

### Post by odwyerda on 2008-11-13
Upgrade via synaptic

---

### Post by Ecologger on 2008-11-13
Yeah I had to do a fresh install because my upgrade was sluggish and it helped, however, thats when my audio problems began.

---

### Post by h0ory0o on 2008-11-16
I just bought a gateway t-6836. So far I love it, but for the past few weeks it has not been starting correctly. When I start the laptop, a black screen shows that says there is a problem starting. Then i have to insert the recovery CD and repair the computer. It does this everytime I start the computer. Is there a way to fix this?

---

### Post by kaoskorruption on 2008-11-24
This really sucks, I upgraded and had the same problems as everybody else. I figured I'd try to wade through them and ask for support but nobody is responding to any of my threads. So far:

-Brightness still doesn't work
-Function keys stopped working
-Resolution stopped working correctly
-It stopped connecting to some networks
-The headphone jack stopped working

This is insane. Updates should make it work BETTER, not WORSE.

---

### Post by kaoskorruption on 2008-11-24
Okay, I fixed the resolution (sort of) by reconfiguring the xorg.conf file. To do this:

```
sudo dpkg-reconfigure xserver-xorg
``` Then reboot. This allows for the resolution of 1280 x 800 (16:10), but that is the only resolution available in widescreen. The other 3:4 resolutions are still there. Fortunately, that is a good resolution that is not too big or small for the average user.

As for the headphone jack, it is working at the moment, but haven't a clue what I did to fix it. All I can say is that I went through the sound settings and checked that none of them were muted. None were, and the sound still didn't work. All I did was reboot and suddenly it worked! Very sketchy.

The internet is also very sketchy. It does work correctly, but DO NOT PRESS Fn + F2. This will disable the wireless internet, but re-enabling it is comparable to the Bermuda Triangle - it either has a VERY delayed response to re-enabling the wireless internet after pressing Fn + F2 OR it just doesn't work at all.

As for the keyboard shortcuts. Go to System -> Preferences -> Keyboard Shortcuts, and update them from there. You unfortunately have to redo all of the sound shortcuts, but it's not that hard. Once you're done, make sure you turn the volume up if necessary. The arrow key, music symbol key, and DVD key refuse to be detected for whatever reason - you probably need some non-existent hardware driver, but they're not that important.

---

### Post by Salvar Fawkes on 2008-11-26
Well, it doesn't automatically detect when the wireless connection has been turned on, but if you uncheck and then recheck "Enable Networking" in the applet in the top right corner, it will find the wireless device again.

The headphone jack problem is really bugging me, though. Also the volume slider gives really weird results... I wonder if there's a way to tell Gnome not to recognize it as a button, but as a slider instead.

---

### Post by nycazncarguy on 2008-12-09
IM BACK.
Sorry for being out for so long...college work caught up with me.

> **kaoskorruption said:**
> This really sucks, I upgraded and had the same problems as everybody else. I figured I'd try to wade through them and ask for support but nobody is responding to any of my threads. So far:

-Brightness still doesn't work
-Function keys stopped working
-Resolution stopped working correctly
-It stopped connecting to some networks
-The headphone jack stopped working

This is insane. Updates should make it work BETTER, not WORSE.

brightness never worked right....but then again, even that program i used to use doesnt work anymore.  There is a way to do it manually, i found out.  I'll explain on the bottom of post.
hmm.....function keys worked for me......iono what happened to yours...
my resolution was fine too...
mine connected to any network i threw at it......
headphone jack......read bottom of my post.

> **kaoskorruption said:**
> Okay, I fixed the resolution (sort of) by reconfiguring the xorg.conf file. To do this:

```
sudo dpkg-reconfigure xserver-xorg
``` Then reboot. This allows for the resolution of 1280 x 800 (16:10), but that is the only resolution available in widescreen. The other 3:4 resolutions are still there. Fortunately, that is a good resolution that is not too big or small for the average user.

As for the headphone jack, it is working at the moment, but haven't a clue what I did to fix it. All I can say is that I went through the sound settings and checked that none of them were muted. None were, and the sound still didn't work. All I did was reboot and suddenly it worked! Very sketchy.

The internet is also very sketchy. It does work correctly, but DO NOT PRESS Fn + F2. This will disable the wireless internet, but re-enabling it is comparable to the Bermuda Triangle - it either has a VERY delayed response to re-enabling the wireless internet after pressing Fn + F2 OR it just doesn't work at all.

As for the keyboard shortcuts. Go to System -> Preferences -> Keyboard Shortcuts, and update them from there. You unfortunately have to redo all of the sound shortcuts, but it's not that hard. Once you're done, make sure you turn the volume up if necessary. The arrow key, music symbol key, and DVD key refuse to be detected for whatever reason - you probably need some non-existent hardware driver, but they're not that important.

What happened to your resolution?  I dont get it.  I hear some of you with resolution problems, yet mine came out fine...lucky me, i guess...
I never used fn+f2, so i wont worry about that.
What keyboard shortcuts do i have to redo?  I don't get it.

> **Salvar Fawkes said:**
> Well, it doesn't automatically detect when the wireless connection has been turned on, but if you uncheck and then recheck "Enable Networking" in the applet in the top right corner, it will find the wireless device again.

The headphone jack problem is really bugging me, though. Also the volume slider gives really weird results... I wonder if there's a way to tell Gnome not to recognize it as a button, but as a slider instead.

The slider thing was always recognized more like a button, no matter which OS you're running.  I wish it could be more like a slider too, but oh well...



Now, for my contribution:
Headphone jack issue
-i thought of something.  I remembered that the first time i tried it, I didnt have anything plugged into the jack.  When i plugged something in, I couldnt hear anything.  However, from then on, I always had my speakers plugged into the headphone jack.  Since then, they've always worked.  So maybe try leaving your headphones/speakers plugged in when you boot up your laptop?  I dunno, it's just a suggestion.  I'm thinking of everything I could've done to make it work.

Screen brightness issue
-I used to use that program called xbacklight mentioned several posts back.  However, upon installing Hardy, it stopped working.  I was looking through the code that allows the laptop to automatically dim as soon as you take off the power cord.  That's when I realized that you can still adjust the brightness.  I warn you though, this is manual work and can be a real pain in the butt if you constantly do it.  Then again, if you only adjust it once in a while, it shouldnt be too bad.

Using the code from the first post to automatically dim the screen upon unplugging the power cord, I was able to paste the same (one) line of code into the terminal to adjust the brightness.

```
 setpci -s 00:02.0 F4.B=FF 
```

You need root access to do this, so just type in sudo before that.  You see the last two letters?  adjust those in accordance to hexadecimal and you can manually adjust the brightness.  Half-brightness is B2.  I'm looking for an alternative fix, hopefully a better one, but for now, this one will do.


Tell me how everything goes :KS

---

### Post by kaoskorruption on 2008-12-09
> The slider thing was always recognized more like a button, no matter which OS you're running.
That's odd because it's definitely more of a slider for me.

Don't worry about the resolution and function keys stuff, they just had to be reconfigured for whatever reason.

As for the headphone jack: After about a month of using the computer, I can honestly say that the headphone jack really doesn't work well enough to be useful whatsoever. When I turn the computer on after being off or restart it, and the headphones are already in it, it works. If I try to put the headphones in after it is already on or if I take them out and then put them back in, they don't work. If I put it into hibernate and then wake it back up they don't work. I've posted two or three topics in the General Help section about this, but none have been answered. Plenty of other people have said they have similar problems, but nobody has found a solution. Let me encourage you all to help me find a solution and to keep asking. This is the most painfully annoying problem that bugs me every single day, and the headphones worked before so I know it is fixable.

---

### Post by nycazncarguy on 2008-12-09
> **kaoskorruption said:**
> That's odd because it's definitely more of a slider for me.

Don't worry about the resolution and function keys stuff, they just had to be reconfigured for whatever reason.

As for the headphone jack: After about a month of using the computer, I can honestly say that the headphone jack really doesn't work well enough to be useful whatsoever. When I turn the computer on after being off or restart it, and the headphones are already in it, it works. If I try to put the headphones in after it is already on or if I take them out and then put them back in, they don't work. If I put it into hibernate and then wake it back up they don't work. I've posted two or three topics in the General Help section about this, but none have been answered. Plenty of other people have said they have similar problems, but nobody has found a solution. Let me encourage you all to help me find a solution and to keep asking. This is the most painfully annoying problem that bugs me every single day, and the headphones worked before so I know it is fixable.

Well, no matter how far towards the plus or minus sign, its always the same speed.  It's like holding down a button.  If you just tap one end, it also only increases a little.  To me, that's like a button.  This is the same for all OSs i've used (I quadboot, so that's alot of proof).  Not that it really matters anyway.  I doubt this is worth arguing...lol.

As for the headphones things, I'm actually interested to hear that.  I dont use hibernate, so i wouldnt know.  But yeah, like i said and as you realized, if you turn on the laptop with it plugged it will work.  Did you try out the brightness thing?

---

### Post by Ecologger on 2008-12-10
The brightness bit works for me. There has got to be a way to create buttons on your top panel for like 100%, 50%, 10%, and so on.
-- You can if you right click the panel and add to panel, custom launcher, and choose application in terminal - put the code in the command box. Still have to input your password through terminal though when you press one. There has got to be a way around that.

---

### Post by Salvar Fawkes on 2008-12-10
The brightness solution works well for me, but it seems kind of dangerous. Can those values be set anywhere from 00 to FF to get the desired brightness, or is there some point at which it'll break something?

The headphone jack thing is a huge problem, but even if I have to reboot after plugging them in, it's better than nothing. That's good to know, although I'm sure I won't use it much.
The thing is, though... everyone always says that the difference between Linux and Windows is that even if something doesn't work, if you know what you're doing there's always a way to fix it in Linux. So what's missing? Is there nobody with this laptop who really knows their way around a soundcard? Is it just a matter of not having the right hardware information from Gateway (or Sigmatel)? Or is this just a matter of Linux enthusiasts overhyping it beyond its abilities?

---

### Post by Ecologger on 2008-12-10
Well it worked in 8.04 flawlessly, so there IS a way to make it work. I am just not enough of an expert to figure out the differences between 8.04 and 8.10.

---

### Post by nycazncarguy on 2008-12-10
the brightness thing has the same potential as the xbacklight program.  If you set it too low, the display light wont turn back on until you restart the laptop.  You can still see the display if you shine a flashlight onto it, so it's just the display light.  That's it.  No harm.  I tried that a while back.  I forgot what the value was though...
Just dont go less than 10%....dunno wat that is in hexadecimal...i doubt its really necessary to go below that.  Otherwise, it wont harm the laptop display.  After all, its used for automatically dimming when running on battery.  I've had no problems with it.

As for the sound card, I really dunno.....maybe there is something we can find in the 8.04 version and compare the differences for the sound card drivers...Just a guess.  My programming isnt good enough to figure that out.

---

### Post by kaoskorruption on 2008-12-10
Well my guess is that anybody that knew their way around Ubuntu would not have gotten this model :P

But anyways, I've opened a bug in launchpad for the headphone part: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755) Feel free to add information or help support me by letting them know that there are a lot of us out there suffering.

As for the brightness: it seems like there must be a way that we can work around it not working. First of all, brightness works flawlessly with Gamma Panel (Windows program in Wine). Why can't Ubuntu do whatever Gamma Panel is doing? I mean, it's a freaking windows program and it works. As for workaround ideas: I think there is some sort of a script that runs when you adjust the brightness, which is just how ubuntu works behind the scenes. If we can find this script file and put in our own commands with xbacklight or whatever, we can make it work. If such a script file doesn't exist, we may be able to create one by having it run a command every time we adjust the brightness through the keyboard shortcuts. Either way you look at, there is no excuse for it not to work. It may be smart for us to open a bug report on launchpad for the brightness part as well.

---

### Post by nycazncarguy on 2008-12-10
well, the funny thing is that the display brightness used to work too.  With xbacklight, that is.  Now, even that program doesnt work anymore, so I'm assuming its not as easy as finding this script.  Otherwise, xbacklight wouldnt have problems not dimming or brightening.  Not only that, the function keys actually recognize that i'm trying to change the brightness setting.  It's just that nothing happens.  If there really is such a script, then we must look for it in 8.04 first.  The program was still working then.  Then we'll see if the file was placed somewhere else or something.

---

### Post by bkanuka on 2008-12-11
Hey I bought a T-6836 as few weeks ago.  Any further gains on any of these issues (all of which I have)??

Did anyone try downgrading the kernel like the Debian guy?? if not I think I will.

---

### Post by bkanuka on 2008-12-11
By golly that was it!!

I enabled old hardy repositories and installed: 
linux-headers-2.6.24-22-generic
linux-image-2.6.24-22-generic
linux-restricted-modules-2.6.24-22-generic
linux-ubuntu-modules-2.6.24-22-generic

rebooted (into 2.6.24) and everything...SOUND HEADPHONES BRIGHTNESS all work.

Later, I edited grub menu.list so that this kernel will be default, and I think this is "problem solved" enough for me.

p.s. I think sound quality is actually better.  Also, still, don't turn your brightness all the way down, it gets stuck.  Know your limits. Stick to them. lol

---

### Post by kaoskorruption on 2008-12-11
So I have to downgrade my computer to make it work? Haha I think Ubuntu has reached a new low.

So when you downgraded, does it basically put back 8.04, or is it just 8.10 with some older packages? Also, wouldn't that make some newer things not work?

---

### Post by bkanuka on 2008-12-11
You're just downgrading the kernel and the corresponding modules. It does NOT revert to 8.04, and quite honestly you are not going to notice any obvious negatives on the surface.

Obviously a better solution would be one which uses the newest kernel, and this is mostly because of security updates but also optimizations which are added in.  I noticed for example a little longer boot time (I'm talking like 2 seconds)...very nominal but there is a point to using new kernels.

It actually is not uncommon to notice regression between Ubuntu or kernel versions. There is a large category on Launchpad devoted to these types of bugs.  Also realize that this is not a "fix" as much as it is duct tape until the bugs get worked out in the current kernel.

Hope this helps.

---

### Post by Ecologger on 2008-12-11
I don't know where you got the restricted modules from but I cannot get them to show up in synaptic.

---

### Post by bkanuka on 2008-12-11
ok ok I can write this up as in a more how-to way.

You need to enable Hardy repositories:

```
sudo gedit /etc/apt/sources.list
```
copy everything you see there, scroll all the way down, and paste it.  Then go through this second half of the file and replace every term "intrepid" with "hardy". There is a find-replace tool for this, just be careful. Then save and close gedit.

```
sudo apt-get update
sudo apt-get install linux-headers-2.6.24-22-generic linux-image-2.6.24-22-generic linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
```

This should work now. Tell me if it doesn't; I wrote this all from memory. Also, if someone has a more elegant way, please tell me.

Then you'll want to reboot your computer and boot into the 2.6.24-22 kernel.  You may need to do this by pressing [Esc] when grub prompts you during boot-up to show menu (I forgot the exact prompt). Then select the 2.6.24-22 kernel (probably at the bottom). When your computer starts back up type in ```
uname -r
``` and make sure the output is "2.6.24-22-generic". This will ensure that you are running the proper kernel. Do a quick check that everything works: brightness, media keys, etc.!

Then to make this kernel default:

```
sudo gedit /boot/grub/menu.lst
```
Scroll through and find the line: 
"title		Ubuntu 8.10, kernel 2.6.24-22-generic"
Select and copy that "paragraph".

Scroll back to the top and find he line:
"# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST"

After this line, hit [Enter] once or twice and then paste the "Ubuntu 8.10, kernel 2.6.24-22-generic" paragraph.  This should not have and #'s and should come before the line "### BEGIN AUTOMAGIC KERNELS LIST".

After that, save close and reboot. When your computer starts back up type in ```
uname -r
``` and make sure the output is "2.6.24-22-generic"

That should be it. Again, post if there's an issue.

---

### Post by Ecologger on 2008-12-11
Well, it sort of works. Gnome brightness works half the time, the other half it is non responsive. Also the gnome power management applet does not work at all and I cannot see how much battery I have left. In addition, the brightness slowly goes up then down then up and so on.

---

### Post by kaoskorruption on 2008-12-11
Well I'm glad that we've found a sort-of fix. I will wait awhile to see if the bug report in launchpad makes any progress before I do this, so that I can help the techs understand what exactly happens. Let's hope they figure something out soon.

---

### Post by bkanuka on 2008-12-11
well my brightness works as it should right now.  I don't know what you mean about it going up and down. You are (kinda) right about the power management.  It acts very strange. It is very slow to respond, and freezes often. It is barely usable.

Any ideas to fix this? maybe we should scower the forums to fix this fix.

Also, we could try a newer kernel. The one I used or recommended IS pretty old and I tried nothing in between. There could be one that fixes everything.

---

### Post by Ecologger on 2008-12-11
What was the last hardy kernel?

---

### Post by bkanuka on 2008-12-11
hihihi I have a fix for power manager acting weird and I think for the dimmer acting weird too! (I did notice the strange dimming right after my previous post).

It has to do with power manager waiting for some ambient light sensor that is not present so it freezes up, also freezing the brightness controls.

kill gnome-power-manager:
```
killall gnome-power-manager 
``` 
open gconf-editor
```
gconf-editor
```
find apps -> gnome-power-manager -> ambient    Uncheck "enable"
also apps -> gnome-power-manager -> backlight  Uncheck "enable"
close gconf
resart gnome-power-manager
```
gnome-power-manager
```

Now I *think* this is going to also stop the screen from automatically adjusting brightness between AC and Battery power.  But the keys work now so it shouldn't be that big of a deal. Also, if you care to I bet you could use the previous fix in the forum for that adjustment to occur.

---

### Post by Ecologger on 2008-12-12
Absolutely genious. It all works, now just stuck with this crummy repository. Can I change it back to intrepid or will that be bad? Also, how did you figure out what was hanging up the power manager?

---

### Post by Ecologger on 2008-12-12
I have run into another problem, maybe you can solve. I keep getting a blank screen and the lines "assuming drive cache: write through" sometimes when I either try to restart, come back from suspend or hibernate. But it is not every time.

---

### Post by bkanuka on 2008-12-12
I don't know what to say about this new problem because I have yet to experience it. It's always easier to fix something when I can run diagnosis on my own. You said it doesn't happen all the time: try to figure out what else changes.

As for discovery, of this ambient light sensor, it came from me fighting through "gnome-power-manager --no-daemon --verbose" and noticing that there were marked slow-downs around the word ambient. The simplicity of the fix was luck. I didn't know where else to change anything about power manager, and gconf just had an option I disabled, and everything worked.

---

### Post by kaoskorruption on 2008-12-12
Well I can tell you that the gnome-power-manager fix doesn't do anything for Ibex.

---

### Post by Ecologger on 2008-12-12
Read [This]("http://wiki.ubuntuforums.org/showthread.php?t=982746") about how to get the Brightness control working in Intrepid. It worked for me so I hope it works for you! Now for the headphone jack......

---

### Post by bkanuka on 2008-12-12
> **kaoskorruption said:**
> Well I can tell you that the gnome-power-manager fix doesn't do anything for Ibex.

Have you downgraded your kernel? The gnome-power-manager fix I have above only fixed something that using the old kernel broke. My power manager worked perfectly before downgrading. But now...in combination...I have everything working: brightness, headphones and power manager. And I'm still running Intrepid.

---

### Post by bkanuka on 2008-12-12
> **Ecologger said:**
> Read [This]("http://wiki.ubuntuforums.org/showthread.php?t=982746") about how to get the Brightness control working in Intrepid. It worked for me so I hope it works for you! Now for the headphone jack......

Hey, have you downgraded your kernel like I recommended before? Because after I did, my headphone jack works perfectly (i.e. more than just once).

I'm asking because I did a LOT to try to fix the headphones before downgrading and so it could be a combination of the config files I messed with and downgrading that fixed it. If we're running the same kernel on the same computer, I wouldn't mind looking through config files to see how I'm set up...

---

### Post by Ecologger on 2008-12-13
I have both the latest and the old kernel installed. The brightness fix was for the latest kernel. I am bouncing back and forth between because in the older kernel I was having some problems shutting down and using some programs in the older kernel.

---

### Post by Ecologger on 2008-12-13
What I have noticed is that the 2.6.24 kernel uses alsa version 1.0.16 and the latest kernel 2.6.26 uses alsa version 1.0.17. So I will try to find a way to switch the version in the latest kernel to see if that works.

---

### Post by bkanuka on 2008-12-13
> **Ecologger said:**
> What I have noticed is that the 2.6.24 kernel uses alsa version 1.0.16 and the latest kernel 2.6.26 uses alsa version 1.0.17. So I will try to find a way to switch the version in the latest kernel to see if that works.

Good idea. I didn't catch that. Also look into which driver/module and version the old kernel uses with the sound card. We could also force the use of this older driver in the new kernel if just downgrading ALSA doesn't fix it.

We're making ground with this...

---

### Post by Ecologger on 2008-12-14
Well, this is harder than it looks. When I first tried to meddle with this, I realized that inorder to install the .deb I got from the hardy repositories, I had to remove the old Alsa driver. However, you have to remove ubuntu-desktop because for some crazy reason they are linked. So I did all that jazz, installed and reinstalled the files I had to remove as collateral. (installed the hardy versions of linux-sound-base, alsa-base, alsa-utils, libasound2, libasound-plugins) Rebooted into the Latest kernel and still no love. I keep getting a version of 1.0.17 when I put in ```
cat /proc/asound/version
``` so I don't know what else to replace. If you do have the .deb files though, I found if you go to the folder where they are located and use the dkpg -i package.deb commands it will install the deb files over the current ones instead of removing all related files. You end up with broken packges this way though. So, I still have not figured it out yet.

---

### Post by bkanuka on 2008-12-14
Alsa might have to be compiled per-kernel, just judging by the output of cat /proc/asound/version in which case you won't be able to use the old .deb...

---

### Post by Ecologger on 2008-12-19
Still not getting anywhere with this issue. I am not confident enough to compile my own kernel at this point and the constant tinkering with my system keeps requiring me to reinstall.

---

### Post by bgilbert on 2008-12-23
It looks like this bug may beyond our ability to fix outside of an actual fix released by the ubuntu developers. If you have any information that you think may be helpful to them in solving this problem please comment on this bug: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

Thanks

---

### Post by enriqg9 on 2008-12-29
Hi, i can use the microphone on Intrepid Ibex with the gateway T6836 but its too low volume, and i ran alsamixer on a terminal and capture its at 100%, does anyone know how to boost the microphone volume for this laptop, because i found on google some tutorials that say how to boost the microphone volume but they doesn't work on the Gateway T6836, Thanks.

I attached my alsamixer config.

[IMG]http://2.bp.blogspot.com/_D4OrNChC82U/SVkZr5S_n0I/AAAAAAAAAFY/DP1FbEpwnY0/s1600/alsa[/IMG]

---

### Post by Ecologger on 2009-01-05
I'm am not sure about the mic because I have never used it on the laptop. I do believe that problem is probably related to the same problem we are having with the headphone jack. Did it work under 8.04?

---

### Post by enriqg9 on 2009-01-09
I dont know i have this laptop since the release of Intrepid Ibex, so i never installed Hardy heron on this Laptop

---

### Post by kaoskorruption on 2009-01-10
After a number of updates to Intrepid, I've been wondering if any of them fix the sound issues that caused us to have to downground our kernals. Some of the updates were for pulseaudio stuff. I don't have the time or courage (haha) to check if the recent updates fixed anything, but I was wondering if anybody happened to know anything.

---

### Post by Ecologger on 2009-01-12
Try Downgrading the kernel or installing 8.04 and see what that gets you.

---

### Post by kaoskorruption on 2009-01-12
Yeah, I already downgraded. What I'm saying is that we wouldn't know if they've fixed it or not in the updates because we are using the workaround of using an old kernel.

---

### Post by bgilbert on 2009-01-14
The problem has not been resolved as of yet, at least the issue with headphones. I didn't downgrade my kernel and I've installed every update thrown my way, yet I'm still plugging in my headphones before I boot my laptop.

Also I believe Ecologger was referring to enriqg9's problem when he suggested downgrading.

---

### Post by psychoelf on 2009-01-16
On a Gateway 6850-FX with the STAC9205 and downgrading kernel fixed the headphone output, but now I cannot dim the screen even after messing with gconf-editor.  Blah.  Damned if you do, damned if you don't.

So what changed between the kernels to cause this?  Or is it just Alsa?  If so you'd think someone would have found a permanent solution by now.

---

### Post by Ecologger on 2009-01-19
We believe that it is the alsa version, which you cannot change in the current kernel version without compiling your own kernel.

---

### Post by psychoelf on 2009-01-19
yeah....I dont think I'll be trying a kernel compile yet.  Still a bit newb to figure that one out.   :P

---

### Post by tu_mas_gordo on 2009-01-20
I don't know whats wrong with some of you guys computers, I was having the same problem with 8.04 and 8.10, I think there is a bios update for our computers on the gateway site. Im not sure if thats what did it but ever since I did the update my headphone jack has always worked. 

Now the only problem I want to fix is dimming the screen problem and making my computer run cooler. What I mean by cooler, I mean my computer pretty much is on full blast as long as it is on. And it gets really hot.

---

### Post by Salvar Fawkes on 2009-01-28
Hey, I think the kernel just updated. I'm in class right now so I can't test the sound, but could someone try it out? Does anyone know where I can find descriptions of Ubuntu updates?

---

### Post by bgilbert on 2009-01-29
The kernel update did not fix the headphones issue for me.

---

### Post by riclags on 2009-01-30
hi all,

i am not sure if this will work for you re the headphone issue but when i installed 8.10, true enough, the headphones didn't work. so i googled around and found 1 way to make it work.

1) right-click on the volume icon (the one on the upper right corner for the sound)
2) on the drop-down list that displays (i think it says ALSA mixer, not sure) look for the option "Surround" and select it
3) in my installation, it was muted. so i unmuted it and put the volume to 100.
4) right-click the volume icon again and select the "Master" option
5) plug in headphones and it will hopefully work

i found this out when i was using xubuntu 8.10 and played around with the different sliders then discovered "Surround" made the headphones work. it was only a matter of finding where Surround was on ubuntu 8.10. and, as described above, i found it...

hope this helps... ;)

btw, i am not using the same laptop model as in this thread...

---

### Post by Salvar Fawkes on 2009-01-31
Yeah, there is no "Surround" option.

---

### Post by asimon623 on 2009-02-04
anybody know if ubuntu is going to fix this issue any time soon? I miss music.

---

### Post by asimon623 on 2009-02-04
weirdest thing is that sound goes through the headphones for the first half second after you plug them in, and then it stops

---

### Post by riclags on 2009-02-05
> **Salvar Fawkes said:**
> Yeah, there is no "Surround" option.

re the "Surround" option, i missed to put it in my suggestion that when you right-click the master volume icon, look for the "Preferences" option. this will open the alsa mixer with all the choices below. look for "Surround" and unmute it then max out it's volume to 100%. i hope this helps. if the "Surround" option is still not there, then i cannot answer that :)

---

### Post by asimon623 on 2009-02-05
yea, I definitely don't have a surround option there.
you have the gateway t-6386 with ubuntu 8.10 w/ update kernel and get sound from the headphone jack?
could you post your entire alsa-base file?

---

### Post by psychoelf on 2009-02-06
From what I understand, it has to do with the version of Alsa in the 8.10 kernel.  I downgraded my kernel using instructions from another poster.  The other option would be compiling an older version of Alsa into the current kernel?  As I know nothing about compiling, I will wait for an update to the kernel to fix this problem.

---

### Post by bgilbert on 2009-02-08
Hey guys,

The bug request for the headphone issue located [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755") is going to be closing in 12 days if no further activity occurs. 

Could any of you guys add a comment with your alsa info or anything else you think may be pertinent so this won't happen? I'd rather it not get closed off prematurely, yet I don't want it to appear that I'm the only guy whose experiencing this problem.

Cheers,
Bryan

---

### Post by kaoskorruption on 2009-02-09
> I don't know whats wrong with some of you guys computers, I was having the same problem with 8.04 and 8.10, I think there is a bios update for our computers on the gateway site. Im not sure if thats what did it but ever since I did the update my headphone jack has always worked.

Now the only problem I want to fix is dimming the screen problem and making my computer run cooler. What I mean by cooler, I mean my computer pretty much is on full blast as long as it is on. And it gets really hot.

Can anyone confirm if this fixed anything?

---

### Post by Ecologger on 2009-02-10
I have not tried because I have important info on my laptop that I would not want to lose. I am always leary of updating/flashing the bios.

---

### Post by asimon623 on 2009-02-10
the flasher is a windows program...
i don't feel comfortable flashing from vmware...

---

### Post by asimon623 on 2009-02-12
what would  i need to append to my alsa-base if i was able to downgrade my kernel?  options ??????.... model =??????

---

### Post by Salvar Fawkes on 2009-02-23
So, what's the process on bug reports? Does it just sit around until someone gets around to it, or it gets forgotten?

---

### Post by kaoskorruption on 2009-03-01
> So, what's the process on bug reports? Does it just sit around until someone gets around to it, or it gets forgotten?

That seems to be the case. From reading some of Ubuntu's press releases, I think that Canonical is more concerned with pleasing their business clients that use the Ubuntu server than the basic desktop. This makes sense though, because this is where they make money, otherwise the entire Ubuntu project would not be possible. All I can say is that I hope it gets fixed in the next release - just 2 months away.

---

### Post by kaoskorruption on 2009-03-27
Anybody daring enough to try 9.04? I'll probably upgrade in May when I have time.

---

### Post by psychoelf on 2009-04-01
9.04 didn't fix it on my 6850fx and I also tried compiling Alsa from source using a script on another thread.  No go.

---

### Post by enriqg9 on 2009-04-13
I upgraded yesterday to Jaunty Beta 64 bits from my Gateway T6836, and the headphone issue its worst, now if i plug the headphones before the booting it also doesn't work, the Video driver its greater than in Intrepid, so it has a better 3d accel with the GMA 945.

---

### Post by kylepotts on 2009-04-13
Thanks dude this really helps. I don't have this model I have a T-6330u. They are pretty much identical.

I could never get the LCD brightness to go down. This guide helped me get the LCD down, and now I have better battery life!

---

### Post by Saghaulor on 2009-04-14
I tried per previous posts, using gconf-editor to disable the ambient lighting feature. It did not help. I also tried to use xbrightness, and that didn't work either. My problem is that my display seems to be too dim, even when plugged in. When I use the function keys to adjust brightness, the slider moves up and down, but nothing changes.

Any ideas?

---

### Post by Saghaulor on 2009-04-14
Btw, I'm using a fully up to date Intrepid amd64.

I seem to have a brighter desktop.

I'm not sure what worked, here's what I did.

1. Used gconf-editor to disable, apps,gnome-power-manager, ambient
2. Per this thread,removed existing gnome-power-manager, installed gnome-power-manager for Hardy amd64. 
[http://ubuntuforums.org/showpost.php?p=6562023&postcount=8](http://ubuntuforums.org/showpost.php?p=6562023&postcount=8)

My function brightness keys are non-responsive now, but I don't really care. I never use them.

When I unplug the ac cord, it doesn't dim the screen. That could be painful.

I'm going to try upgrading to Jaunty in the next few days. Hopefully it works better. I'll report back.

---

### Post by Salvar Fawkes on 2009-04-17
The hack in the original post has worked like a charm for me so far. It's probably unsafe, technically, but nothing else works. I changed the value a bit, too, and my battery finally lasts longer than it takes to charge.

---

### Post by nycazncarguy on 2009-04-27
okay, just upgraded to 9.04.

headphone issue, as it has been stated above, just got worse. does not work if its plugged in to begin with.

lighting issue - nothing has changed.

okay, iono if its just my computer....but has your desktop effects just stopped working? like, i have no cube anymore, no minimizing effects, nothing. nada. i uninstalled the compizconfig manager i had that worked in the last version, tried using ubuntu's native setting choices. when i tried that, it just said something about it not being able to load. i reinstalled the compizconfig manager, but still same issue..
i'd like your inputs on this guys.  thanks.

otherwise, it certainly runs faster. i can feel it. prettier too! =)

---

### Post by Le Rob on 2009-04-29
> **nycazncarguy said:**
> okay, just upgraded to 9.04.

headphone issue, as it has been stated above, just got worse. does not work if its plugged in to begin with.

lighting issue - nothing has changed.

okay, iono if its just my computer....but has your desktop effects just stopped working? like, i have no cube anymore, no minimizing effects, nothing. nada. i uninstalled the compizconfig manager i had that worked in the last version, tried using ubuntu's native setting choices. when i tried that, it just said something about it not being able to load. i reinstalled the compizconfig manager, but still same issue..
i'd like your inputs on this guys.  thanks.

otherwise, it certainly runs faster. i can feel it. prettier too! =)

I can confirm that everything that was an issue is now an issue. In fact, it's worse, as pointed out: headphones don't even worked if plugged in on startup. Also, I can confirm nycazncarguy's issue--compiz no longer seems to work. I hadn't used it before, so I didn't notice until I tried to run it from terminal to get some basic debugging information. It crashed gdm, so I don't recommend it if you can avoid it, but I can tell you beyond all reasonable doubt it's because the graphics card in the T-68x8 series is now blacklisted for compiz (if I recall correctly, it's the Intel GM965 in the T-6828).

Also, I've tried to use OSS4.1 to resolve the sound issues. If you're desperate, it might work, but to be honest I found it presented far too many sound issues. For starters, there was no jack sense, so, while you'd get headphones, the front wouldn't automatically mute, and issues specifically with the 6828 meant that it was impossible to turn down the front without turning down the headphones. Secondly, apps using phonon (or anything using the HAL), such as Amarok, don't play--that is, HAL refuses to provide support for OSS until they support udev and sysfs. It should be noted that the sound quality on OSS was superior, at least to this audiophile's ears, but there was clearly issues with multiplexing (i.e. you couldn't listen to two different songs at one time and have them both play) that would make this only worth it if the headphones worked perfectly. My advice: stay clear for right now; it's not worth the effort to get it going.

Also tried: flashing the new BIOS (released August 2008). No such luck, though it's nice to have the latest version.

It should also be noted, for future workarounds, that Jaunty ships with ALSA 1.0.18.rc3. 1.0.19 is out, and I'll try that tonight yet.

On the upside: though the brightness buttons don't work, the screen looks fantastic. Crystal clear; looks nicer than Windows. My computer also loads faster (ext4 for the win--they said it was only going to speed things up 10-20%--well, I'm seeing at least a 50-75% boost...), and runs cooler. 

Another thing noted: if you're doing the update and are installing Amarok, you will need libxine1-ffmpeg. Threw me for a loop at the start.

More coming soon.

---

### Post by Le Rob on 2009-04-29
Some progress: first and foremost, I managed to get the next version of ALSA installed with no problems (there's a handy script at [this thread](http://ubuntuforums.org/showthread.php?p=6589810#post6589810). I found no immediate solution to any of the problems.

However, I've managed to get my headphone jack working if nothing else. I don't know if the 6838 has as many confusing options as the 6828, but my laptop has 6 different sound devices, and the ones you can manipulate are, in no particular order:

HDA Intel (ALSA Mixer)
SigmaTel STAC9205 (OSS Mixer)
Playback: HDA Intel -- STAC92xx Analog (PulseAudio Mixebottr)
Capture: Monitor of HDA Intel -- STAC92xx Analog (PulseAudio Mixer)
Capture: HDA Intel -- STAC92xx Analog (PulseAudio Mixer)

The bottom three obviously deal with PulseAudio, which essentially works to patch sound from one source to another. I made sure the volumes were up to maximum on all of them (I'd rather deal with the primary sources, rather than secondary). You can mostly ignore the OSS Mixer. In the ALSA Mixer, make sure you've enabled the 'Capture', 'Digital', and 'Mux' sliders in preferences--ignore 'Capture 1' and 'Mux 1'; they're useless, as far as things go. Start with them on lowest volume, but make sure they're not muted. When 'Capture' and 'Mux' were at the highest, I was getting a piddly little sound until I unmuted 'Digital' and cranked it to its highest, but results may vary: I was using the awful little speakers on the laptop's front.

Also, you need to make sure that you've enabled 'Digital Input Source' in preferences, and set it to 'Digital Mic 1', not 'Analog'.

The recording was still pretty quiet, but I chalk that up to the actual microphone itself. This is good news, though--the microphone didn't work in Windows in the first place.

More to come in regards to making ALSA 1.0.19 work.

EDIT: Addendum--make sure you have 'Analog Loopback' **disabled**, or you'll suffer some terrible feedback.

---

### Post by nycazncarguy on 2009-04-29
> **Le Rob said:**
> Some progress: first and foremost, I managed to get the next version of ALSA installed with no problems (there's a handy script at [this thread](http://ubuntuforums.org/showthread.php?p=6589810#post6589810). I found no immediate solution to any of the problems.

However, I've managed to get my headphone jack working if nothing else. I don't know if the 6838 has as many confusing options as the 6828, but my laptop has 6 different sound devices, and the ones you can manipulate are, in no particular order:

HDA Intel (ALSA Mixer)
SigmaTel STAC9205 (OSS Mixer)
Playback: HDA Intel -- STAC92xx Analog (PulseAudio Mixebottr)
Capture: Monitor of HDA Intel -- STAC92xx Analog (PulseAudio Mixer)
Capture: HDA Intel -- STAC92xx Analog (PulseAudio Mixer)

The bottom three obviously deal with PulseAudio, which essentially works to patch sound from one source to another. I made sure the volumes were up to maximum on all of them (I'd rather deal with the primary sources, rather than secondary). You can mostly ignore the OSS Mixer. In the ALSA Mixer, make sure you've enabled the 'Capture', 'Digital', and 'Mux' sliders in preferences--ignore 'Capture 1' and 'Mux 1'; they're useless, as far as things go. Start with them on lowest volume, but make sure they're not muted. When 'Capture' and 'Mux' were at the highest, I was getting a piddly little sound until I unmuted 'Digital' and cranked it to its highest, but results may vary: I was using the awful little speakers on the laptop's front.

Also, you need to make sure that you've enabled 'Digital Input Source' in preferences, and set it to 'Digital Mic 1', not 'Analog'.

The recording was still pretty quiet, but I chalk that up to the actual microphone itself. This is good news, though--the microphone didn't work in Windows in the first place.

More to come in regards to making ALSA 1.0.19 work.

EDIT: Addendum--make sure you have 'Analog Loopback' **disabled**, or you'll suffer some terrible feedback.

Sounds interesting.  I'll give that a try tonight after I nap (yes, at night).  Running one 1hr of sleep from 18 hrs ago...stupid class registration..What kind of college sets class registration at 6am?? and has a teacher who gives a hard test the same day 3 hrs later? ANYWAY

Sorry for getting off-topic.  And yeah, those are the same FIVE, not six, (its okay, minor thing) that I have. Or something like that.  In windows right now, so cant check at the moment.  I only use headphone jack anyway.  I have them hooked up to the external speakers. I'm pretty sure I speak for all of us when I say this: the built-in speakers on this thing sucks.

I havent tried this with the new alsa, obviously, as I'm still in windows, but I remember trying skype a couple days back. webcam works, but i got some audio problems? I couldnt do a test call. I heard music from amarok from built-in speakers fine tho, so I dunno what that was about.  Any clue?

No compiz working is a huge bummer for me.  I use expo alot..sigh.

---

### Post by Le Rob on 2009-04-29
I meant what I said, actually, though I can see why it might have confused you. There are actually six different devices that show up when running diagnostics; the five that I listed are just the entries on the volume control, and correspond to the actual soundcard, a STAC9205. Sorry for being unclear, but if we have the same devices across the 6828 and the 6838, this is good news(ish)--it means that the bug affects a broader range of users, and we can correspondingly demand a bit more attention from the devs.

At this point, I don't see any point in upgrading ALSA to 1.0.19. It'll hit the repositories soon enough, I suppose, and if the only fix is downgrading to 1.0.16 vis-a-vis a custom-rolled kernel, then why trouble yourself? 

The webcam does work, and I believe that the earlier recommendation of the program 'Cheese' is one to reiterate.

You say that it works with external speakers? Can you confirm that it doesn't work with headphones? Also, are your external speakers powered by an AC adaptor/batteries (as opposed to drawing power from the computer)? If you confirm both, it would seem that the issue is related to powering the jacks, and that's an important distinction to make for the devs.

As to Compiz, a simple search vindicated me: you can see that the Intel 965 is on the blacklist. You can force-enable it by following the instructions listed [here](http://wiki.opencompositing.org/Hardware/Blacklist), but with the caveat that if you hose your system, it's your own fault. I doubt it will come to that, though, and if you have your desktop (GDM) crash on you, you can press CTRL+ALT+F1, log in, and type ```
sudo killall gdm && sudo gdm
```. Also, if you chose to store the value in ~/.config/compiz/compiz-manager, you can run ```
nano -w ~/.config/compiz/compiz-manager
``` to remove the line, and then save/exit with Ctrl+O Ctrl+X.

---

### Post by nycazncarguy on 2009-04-30
> **Le Rob said:**
> I meant what I said, actually, though I can see why it might have confused you. There are actually six different devices that show up when running diagnostics; the five that I listed are just the entries on the volume control, and correspond to the actual soundcard, a STAC9205. Sorry for being unclear, but if we have the same devices across the 6828 and the 6838, this is good news(ish)--it means that the bug affects a broader range of users, and we can correspondingly demand a bit more attention from the devs.

At this point, I don't see any point in upgrading ALSA to 1.0.19. It'll hit the repositories soon enough, I suppose, and if the only fix is downgrading to 1.0.16 vis-a-vis a custom-rolled kernel, then why trouble yourself? 

The webcam does work, and I believe that the earlier recommendation of the program 'Cheese' is one to reiterate.

You say that it works with external speakers? Can you confirm that it doesn't work with headphones? Also, are your external speakers powered by an AC adaptor/batteries (as opposed to drawing power from the computer)? If you confirm both, it would seem that the issue is related to powering the jacks, and that's an important distinction to make for the devs.

As to Compiz, a simple search vindicated me: you can see that the Intel 965 is on the blacklist. You can force-enable it by following the instructions listed [here](http://wiki.opencompositing.org/Hardware/Blacklist), but with the caveat that if you hose your system, it's your own fault. I doubt it will come to that, though, and if you have your desktop (GDM) crash on you, you can press CTRL+ALT+F1, log in, and type ```
sudo killall gdm && sudo gdm
```. Also, if you chose to store the value in ~/.config/compiz/compiz-manager, you can run ```
nano -w ~/.config/compiz/compiz-manager
``` to remove the line, and then save/exit with Ctrl+O Ctrl+X.

Haha, okay, my bad.

And no, the webcam works without cheese. it worked in skype!  I didnt even open up cheese.  I saw myself in the skype preferences video setup.

And no, I didnt say i heard sound through my externals...lol.  I heard sound from my built-in speakers.  I was just saying that I generally use my external speakers for this laptop, regardless of the OS.  Sorry for not clarifying that.  And if it still matters, my speakers run off an external power supply.

I'm definitely trying out that compiz override.  I use it too much..lol.  Thanks for that.  I'll be trying it out later tonight.

---

### Post by c_wilson on 2009-05-02
First, thanks to everyone in the thread - helped me get my t-6836 up and running with 8.04, very helpful.

Now i'm on a fresh install of 9.04 x64 and having pretty much the same trouble as everyone else. 

I successfully upgraded to the latest alsa, 1.0.19, and the headphone jack still does not work. PC speakers still work. 

Compiz has also stopped working though it was working with the RC.

I also wanted to note, in case it saves someone some time, that the headphone issue is present in a bunch of other distros. I've installed fedora 10, then upgraded to 11, no luck. Also tried sidux 2009-01, openSUSE 11.1, Mandriva 2009 spring off of live media, same story. 

Sounds like downgrading the kernel was working OK in 8.10, anyone try it on jaunty? I'm going to give that a shot or maybe just reinstall 8.04.

Normally don't mind a few hardware snafus, but the headphones not working is a real show stopper for me. bummer.

---

### Post by Xombie207 on 2009-05-11
I tried to install kubuntu with two different discs and they wouldn't work on my t6836...they both froze at the boot menu after u choose what language u want...i just reinstalled intrepid 64 bit and upgraded to jaunty and then installed the kubuntu-desktop package...i was using gnome, but im going back to kde...

---

### Post by Salvar Fawkes on 2009-05-12
I upgraded to Jaunty because everyone was raving about it, but now I find out that it breaks existing functionality. This is just ridiculous. Does there exist an easy "downgrade" function, or am I looking at a complete reinstall?

---

### Post by kaoskorruption on 2009-05-20
This is the second update where functionality decreased. The last one created major sound issues as well, but we were able to fix them. Hopefully we can do it again, but who knows.

---

### Post by Le Rob on 2009-05-22
UPDATE ON HEADPHONES IN JAUNTY: There was a message on Bugzilla today by a person who has managed to get their headphones working. It has been confirmed to work by a few people, and I'm doing it myself right now. I'll let you know if it works.

The solution can be found [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755).

EDIT: Sadly, this does not work on the T-6828. However, I urge others to try it with their laptops.

EDIT EDIT: With the addition of a line to my /etc/modprobe.d/alsa-base.conf file, I can confirm that **this headphone fix works** for the T-6828. Make sure you append:

```
options snd-hda-intel enable_msi=0 model=eapd
```

... to the end of that file, and reboot. (Theoretically, I think the enable_msi=0 line could be removed, but I'm not about to play with something when it works...)

---

### Post by c_wilson on 2009-05-23
WHOOOOOOOOOHHHOOOOOOOOOOOO:D

err, just wanted to confirm that this works on gateway t-6836 (with the alsa-upgrade script and that line from Le Rob in your alsa.conf)

Thanks!!

Edit: on jaunty 64

---

### Post by Le Rob on 2009-05-23
Some people on the bug thread have noted that flash sound breaks when you update to 1.0.20. However, I've not experienced this issue; I attribute it to upgrading to the latest snapshot (invoke the ALSA script with -snap instead of -di).

---

### Post by enriqg9 on 2009-05-23
CONFIRMED!!!!!!!!!!!!!!!!!! Downloading the Script and adding the line options snd-hda-intel enable_msi=0 model=eapd To the finish of /etc/modprobe.d/alsa-base.conf, FIXES CORRECTLY the Headphone issue of the Gateway T-6836 Running Ubuntu 9.04 Jaunty Jackalope 64 Bits. Thanks i was waiting for this solution since a long time ago...

---

### Post by Salvar Fawkes on 2009-05-23
That's a relief. Now if we could just get Compiz back...

---

### Post by Salvar Fawkes on 2009-06-05
Has anyone tried using UXA on the T-6386? It seems like a simple task to switch it on, or off again, so I'm thinking about trying it out. I'm starting to get the impression that the Intel bug isn't going to be fixed before Karmic, if then. If UXA doesn't work I might just do a fresh reinstall of Intrepid again... better than going without Compiz for years...

---

### Post by Salvar Fawkes on 2009-06-08
Hey, progress on the graphics front. I've had some luck with this package:
[https://launchpad.net/~bryceharrington/+archive/green](https://launchpad.net/~bryceharrington/+archive/green)

---

### Post by c_wilson on 2009-06-12
Inadvertently got the screen brightness adjustment working today! 

In a half-hearted attempt to get compiz working again i followed [this guide]("http://ubuntuforums.org/showthread.php?t=1130582") ([http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)). 

I followed the "Optimal" solution and alas, still no desktop effects, but i was thrilled to find that backlight brightness is now functioning. The screen will dim when idle and when you unplug from AC power (assuming you have power management set up this way). The manual keyboard control also works, but is agonizingly slow.

The "Optimal" solution in the above guide has you change some settings in xorg.conf and then upgrade your kernel to 2.6.30. As far as i can tell, this hasn't broken anything, but i've only been using this setup for a short time.

Edit: i took out the changes to xorg.conf and backlight brightness still works, so it looks like just upgrading the kernel will do it.

Also, UXA acceleration was part of the above fix, so that does not appear to fix compiz.

---

### Post by kaoskorruption on 2009-06-12
Is anyone having a problem with totem? Anytime I try to play a video in Totem, it causes Ubuntu to crash so that it goes back to the login screen. It usually takes awhile before it crashes though - say, for example, after 30 seconds of video playback.

---

### Post by c_wilson on 2009-06-13
> **kaoskorruption said:**
> Is anyone having a problem with totem? Anytime I try to play a video in Totem, it causes Ubuntu to crash so that it goes back to the login screen. It usually takes awhile before it crashes though - say, for example, after 30 seconds of video playback.

I can only report that vlc seems to be working fine.

---

### Post by enriqg9 on 2009-06-17
> **kaoskorruption said:**
> Is anyone having a problem with totem? Anytime I try to play a video in Totem, it causes Ubuntu to crash so that it goes back to the login screen. It usually takes awhile before it crashes though - say, for example, after 30 seconds of video playback.

Have you tried with totem-xine instead of totem?

---

### Post by enriqg9 on 2009-06-21
Am i the only one who gets jaunty freezing suddlenly and randomly? when jaunty freezes i can only move the mouse but i cant use the keyboard, and no application responds. Im using the Gateway T-6836 with Jaunty on EXT4

---

### Post by enriqg9 on 2009-06-23
Upgrading Jaunty to kernel 2.28.13 removes the Audio from the Headphone Jack again! Does any one knows how to solve this again on the 2.28.13 kernel?
----------------------------------------------------------------------------
EDITED

Upgrading to Kernel 2.6.30 Fixes again the headphone jack problem, and its said that it also fixes the freezing screen in Jaunty. You can update your kernel to 2.6.30 following [This Link]("http://portalubuntu.blogspot.com/2009/06/instalar-kernel-2630-en-ubuntu.html")

---

### Post by Nelsinius on 2009-07-01
I have a Gateway MA3 Laptop running Ubuntu 9.04 using an external USB hard drive. I have to give a presentation (OpenOffice.org Presentation) using a video projector, but I am unable to output video through the VGA port. The Laptop's VGA controller is as follows: ATI Technologies Inc RS482 [ Radeon Xpress 200M]. Please indicate a simple way to enable the VGA port with with my hardware. In an older, different kind of laptop I used to code "$sudo i810 switch crt on" to enable VGA.

---

### Post by c_wilson on 2009-07-02
> **Nelsinius said:**
> I have a Gateway MA3 Laptop running Ubuntu 9.04 using an external USB hard drive. I have to give a presentation (OpenOffice.org Presentation) using a video projector, but I am unable to output video through the VGA port. The Laptop's VGA controller is as follows: ATI Technologies Inc RS482 [ Radeon Xpress 200M]. Please indicate a simple way to enable the VGA port with with my hardware. In an older, different kind of laptop I used to code "$sudo i810 switch crt on" to enable VGA.

Just to be clear, you've already tried - System > Preferences > Display?

---

### Post by Nelsinius on 2009-07-02
I entered in a Terminal the following code to find out what were my options: $xrandr -q
Then I entered the following code to enable the VGA port:
$ xrandr --output VGA-0 --mode [a specific resolution identified in the previous step].
The problem I have now is that the resolution for the projector is suboptimal (i.e., I cannot see the right side of my desktop, and xrandr does not recognize the resolution that I need).

---

### Post by kaoskorruption on 2009-07-05
boop

---

### Post by kaoskorruption on 2009-07-07
Hey folks, I've made a new forum thread for 9.04 for the T-6836. You can find it [here]("http://ubuntuforums.org/showthread.php?p=7574382#post7574382"). Let's continue the discussion there.

---

### Post by kaoskorruption on 2009-08-12
My sound suddenly stopped working completely. I suspect a recent update. Has this happened to anyone?

---

### Post by Genecks on 2009-12-26
UPDATE: audio and lighting

I seemed to have found a crappy workaround for the lighting.
If all of you want to play with installing kernels and trying to find the right one, then you can do that.

First off, I installed kernel 2.6.32.1 today.
Yes, it's quite early, but I did it anyway, because I want to be a cool kid.

It seems like the headphones are fixed, but playing a video can cause some kind of weird lag. Opening the same music video again seems to fix the issue. I don't know what the issue is. I can indeed pull the headphones out and in and out and keep sound going. Awesome. No need for that alsa update with the 2.6.32.1 kernel I manually installed.

I added this line to my boot parameter

acpi_backlight=vendor

See?

```
title		Debian GNU/Linux, kernel 2.6.32.1
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32.1 root=UUID=f1c2f7dc-7e86-464d-87c6-9c229a412ca4 ro quiet acpi_backlight=vendor
```

Then I went into gconf-editor via terminal

Get into /apps/metacity

Go into global_keybindings

/apps/metacity/global_keybindings/run_command_1 
value = 0x65

/apps/metacity/global_keybindings/run_command_2
value = 0xd4

/apps/metacity/global_keybindings/run_command_3
value = XF86Display

then go to keybinding_commands folder
/apps/metacity/keybinding_commands/command_1
value=/apps/metacity/keybinding_commands/command_1
/apps/metacity/keybinding_commands/command_2
value=xbacklight -inc 3
/apps/metacity/keybinding_commands/command_3
value=xbacklight -set 100

Fn up = increase light
Fn down = decrease light

Problems: some cpu lag occurs from playing with the decreasing and increasing. Sometimes increments are more than desire, so be careful not to blackout the screen. I would not suggest you hold down Fn and down key. Tap the down key.

Fn and F4 together set the lighting to 100%

I found the keybindings by playing with keyboard shortcuts. For volume mute, I played with Fn and down. It gave me a value, and I used that value as the key binding value for decreasing light. Your values might be different because of ubuntu; i'm on debian. but whatever. You'll figure it out.

---

### Post by odwyerda on 2010-01-11
Fixed
....

---

