---
title: "NVIDIA X Server Settings"
date: 2008-08-04
forum: General Help
---

### Post by zippy_uk_2001 on 2008-08-04
Hi All, 

Got a real numpty X11 issue if anyone has a min...

Running Hardy
Linux compaq-ubuntu 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
nVidia Corporation G71 [GeForce 7300 GS] with Proview 770 monitor

Everything was all lovely - had my wobbly windows, my spinning cube desktop; friends were suitably impressed - the world was a great place ...then I got all clever! I tried to set up my second display - bang! I'd stuffed it.

Spent ages trying to get the dual screen, following various articles with no joy. Given up on that for now (will try again in a few versions), but the problem is trying to get back to square one, but I'm caught in a loop.

So, here's what I'm doing...

Go into hardware drivers, and enable the "Nvidia Accelerated graphics driver" - cool, the enabled check box is ticked and I get the green tick for 'in use'.

It wants a reboot - cool, do that, but coming back up I get a little GUI  informing me that Ubuntu is running in low graphics mode, asking me to configure my card and display, or cancel. It doesn't seem to matter if I configure the card and the screen as asked or not.  

So, at this point I've either configured or not configured the graphics setting during start up.

Box continues to come back up, but now I've only got 800x600 (or 640 x 480) We stay positive though, check the hardware drivers, still enabled and in use – cool.

Go into  Administration &#8594; Nvidia X Server Settings, Get the message that I'm not using the Nvidia X Driver, and I should run Nvidia-xconfig ...which I do
Using X configuration file: "/etc/X11/xorg.conf".
#Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Need to restart X server – so I log out, or reboot, or run /etc/init.d/gdm restart

Get back to the “Ubuntu running in low graphics mode” config screen I had earlier and we start the loop again.

I've tried the “sudo dpkg-reconfigure xserver-xorg” which gets me back to a good resolution again, but has disabled the Hardware Drivers, and the Nvidia  X Server settings are still saying that I'm not running the X driver.

The key to the problem seems to be in that config screen, but it's not exactly complicated – select the  card and the screen – should be easy. 

My next logical step is a rebuild, but apart from these graphics issues she's running sweet, the family all have their own accounts, with mails and everything moved off Windows, so I a rebuild is going  to be a lot of faff. 

All help gratefully appreciated 

Ta,
Ash

---

### Post by MrHippocampus on 2008-08-04
Can you post your xorg.conf after running "sudo dpkg-reconfigure xserver-xorg", as in one which works but isn't using the nvidia driver? From there it should be possible to edit it manually to use the nvidia driver (as well as dual screens).

---

### Post by tetrafuran on 2008-08-04
I have exactly the same problem as zippy_uk_2001. Has anyone stumbled upon any solutions?

---

### Post by RedRat on 2008-08-04
I had a problem too of not getting the nVidia setting to "stick". I found that I had to download and install Nvidia-settings tool. You install it then when you go to run it, you must run it as administrator other wise changes to the conf file don't take.
you must run: gksudo nvidia-settings
After you make your settings, you must save and quit. Hope this helps

---

### Post by ahave2005 on 2008-08-05
I've had this problem as well, twice. It all started when i enabled desktop effects. And yes you get a loop, from which there seems to be no other solutions but reinstall. I also had strange graphic errors on the desktop.

I tried everything I new of, had a copy of xorg.conf. Didn't help. tried the vesa driver, no luck.

Finally I uninstalled xserver-xgl, and bingo a restart and everything was back to normal.

Dual monitor setup, Nvidia 7600GT. I did try with only one monitor, but it was the same.

So no desktop effects for me. Not that it matters that much.

Everything was working fine in 7.10.

/ahave

---

### Post by tetrafuran on 2008-08-07
That gave me an idea. I tried to use gksudo displayconfig-gtk, but apparently that settings menu stil doesn't remember any settings I give it. well.. it was worth a shot.

Another thing was a fresh re-install of the entire system. It solved the driver issues, but apparently every time I try to update some software, the system freezes. Occasionally it even freezed before logging in. Fortunately I somehow managed to get those updates done.

---

### Post by wd5gnr on 2008-08-07
Two things that might help.

First of all the nvidia-settings panel only saves things when you are root. So sudo nvidia-settings.

Second, I had a terrible time getting my 2nd screen out of 640x480. The problem was whatever detects the display wasn't reading the info right so the scan frequency was way off on the 2nd monitor. 

So I had like
HorizSync   25.0-31.0

In my xorg.conf (something like that -- I don't remember the exact numbers). Look up your monitor (if possible) and change it to be something like:

HorizSync 31.0-80.0

Of course, you have to restart the X server, yada yada....

---

### Post by zippy_uk_2001 on 2008-08-08
Thanks for the replies all - at least it sounds like I'm not missing something obvious. 

There's a few things there to try out - I'll let you know if I can get any of them to work.

Cheers,
Ash

---

### Post by zippy_uk_2001 on 2008-08-08
Well, didn't fix it, but did learn the gksudo command which I hadn't seen before - like that.

Adding to what we've chatted about above, I also tried uninstalling anything I could find with Nvidia connections and re-installing, but no change,

So as other people have got dual monitors running, it appears to be something local to either the Nvidia card, or the drivers.

I'll see if I can find an ATI card knocking about the place to see if I get any different results (I'll post if I do), but failing that I may aswell rebuild. The amount of time I've spent trying to save my pride I could have done it a few times by now :-)

Cheers for the help though all - it's apreciated =D>

Ash

---

### Post by struess on 2008-08-09
hey.. check out this thread:

[http://ubuntuforums.org/showthread.php?t=851446&highlight=nvidia+server+enable+dual+monitor]("http://ubuntuforums.org/showthread.php?t=851446&highlight=nvidia+server+enable+dual+monitor")

i had the same problem, and the solution was to enable xinerama under root and save the config file.  

NOTE:  if you want to launch a program outside of a terminal in root, as suggested in the above link, **use the gksudo command, not sudo.**

good luck!

---

### Post by Pippinuk on 2008-08-10
Check out this post:

[http://ubuntuforums.org/showthread.php?t=885015&highlight=Dual+Monitors](http://ubuntuforums.org/showthread.php?t=885015&highlight=Dual+Monitors)

---

### Post by RedRat on 2008-08-10
> **Pippinuk said:**
> Check out this post:

[http://ubuntuforums.org/showthread.php?t=885015&highlight=Dual+Monitors](http://ubuntuforums.org/showthread.php?t=885015&highlight=Dual+Monitors)

OK, installed Envy and the nvidia-enby drivers. However, when running Firefox, the application is really, really slow and lethargic. Takes quite awhile to load web sites. In my machine running an 8600GT card, Firefox seems to pulse, getting lighter and then darker, which indicates a possible memory problem.

Anyone have any ideas how to get Firefox back to normal.

---

### Post by RedRat on 2008-08-10
> **RedRat said:**
> OK, installed Envy and the nvidia-enby drivers. However, when running Firefox, the application is really, really slow and lethargic. Takes quite awhile to load web sites. In my machine running an 8600GT card, Firefox seems to pulse, getting lighter and then darker, which indicates a possible memory problem.

Anyone have any ideas how to get Firefox back to normal.

OK, I seem to have resolved this issue. Initially I thought it was the Envy driver installation so I went in to Hardware settings and enabled the Proprietary driver from NVidia. On restart the system went into the toilet. My screen resolution was 640x480 or 800x600, a mess. I could not access the System files in the menu on top. So I re-installed the Envy drivers and on re-boot, all was kinda OK. the log-in screen was off to the right. When the system came up it looked ok but again Firefox did not work correctly. 

I went into nvidia-settings (gksudo nvidia-settings) and took a look at the monitor settings. Somehow, Envy had set the refresh rate of my Samsung 191t to 75Hz. So I set it back to 60Hz. When I did this, Firefox appeared to now work OK. I will check my other graphics programs and see if they too work OK.

Does anyone have thoughts on this???

---

### Post by Xan63 on 2008-08-15
I'm quite interested in this thread, I'm experiencing almost the same issues!

@RedRat> In my machine running an 8600GT cardAs I am currently experiencing the same kind of issues with my 8600GT card (I never reached to access to Nvidia Settings), could you tell me which version of Nvidia driver you are using?

You finally managed to get a proper install with Envy, isn't it?Because I tried many times, and I got no success :(

> I found that I had to download and install Nvidia-settings tool. 

> If I understand well, to fix all the issues, you followed the following steps:
- install Nvidia drivers with Envy
- install nvidia-settings tools (do you mean nvidia-xconfig nvidia-settings ?)
- gksudo nvidia-settings

Just a question: If I try to install nvidia-settings, it tells me that  nvidia-glx will be removed.
Could this hose my box?

And is the removing of xserver-xgl really necessary?

Thanks by advance!

---

### Post by RedRat on 2008-08-15
> **Xan63 said:**
> I'm quite interested in this thread, I'm experiencing almost the same issues!

@RedRatAs I am currently experiencing the same kind of issues with my 8600GT card (I never reached to access to Nvidia Settings), could you tell me which version of Nvidia driver you are using?

You finally managed to get a proper install with Envy, isn't it?Because I tried many times, and I got no success :(

 

> If I understand well, to fix all the issues, you followed the following steps:
- install Nvidia drivers with Envy
- install nvidia-settings tools (do you mean nvidia-xconfig nvidia-settings ?)
- gksudo nvidia-settings

Just a question: If I try to install nvidia-settings, it tells me that  nvidia-glx will be removed.
Could this hose my box?

And is the removing of xserver-xgl really necessary?

Thanks by advance!

Well here's the thing, I did install the envy drivers and they appear to work great. I will probably stick with them since they actually seem to have slightly better performance than the ones from NVidia. When I first experienced the problem with Firefox (and still do not understand why the refresh rate should be a problem) I thought that I would switch back to the other proprietary drivers. I went to System>Administration>Hardware drivers and enabled them and then re-started my machine. All hell broke loose. My system restarted in very low resolution mode and I had a deuce of a time getting to anything on my desktop. So instead of fighting it, I re-installed the envy drivers because I could only reach Applications in the top menu, none of the other menu items were reachable.

After I got envy back, I went to nvidia-settings, using the gksudo command, entered the password so you are doing it as root otherwise it will not copy over the xorg.conf file. More out of desperation, I switched my screen resolution back to 60Hz refresh and it cleared up the Firefox problem.

OK, that being said, If your current drivers are working fine stick with them. As to setting the card, you have to download nvidia-settings, you can get it from synaptic. In the Terminal, run gksudo nvidia-settings. Set you screen resolution and refresh rate and then save the file. You will see that you can just go to Terminal and run nvidia-settings, but the copy of xorg.conf will not stick. Need to do it as root, it's a permission thing.

BTW, I really stumbled on all of the hoo-hahing around by pure accident since there is nothing written down about these drivers that I was able to find. Might be somewhere in here in the forums but I didn't find it.

---

### Post by Xan63 on 2008-08-15
> I did install the envy drivers and they appear to work great.
> Which version of drivers did you take in Envy?173.14.12? or an earlier version?

> In the Terminal, run gksudo nvidia-settings After dl and install nvidia-settings & nvidia-xconfig, when I'm tryin gksudo nvidia-settings, I obtain the following result:

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

> I tried to do 
```
sudo nvidia-xconfig
Using X configuration file: "/home/xan/xorg.conf".
Backed up file '/home/xan/xorg.conf' as '/home/xan/xorg.conf.backup'
New X configuration file written to '/home/xan/xorg.conf'

```
=> After stop and restart gdm, it still gives me the same result.

Here is my xorg.conf:

```

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
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
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

I don't see what I could do to find an solution... :|

---

### Post by RedRat on 2008-08-15
> **Xan63 said:**
> > Which version of drivers did you take in Envy?173.14.12? or an earlier version?

 After dl and install nvidia-settings & nvidia-xconfig, when I'm tryin gksudo nvidia-settings, I obtain the following result:

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

> I tried to do 
```
sudo nvidia-xconfig
Using X configuration file: "/home/xan/xorg.conf".
Backed up file '/home/xan/xorg.conf' as '/home/xan/xorg.conf.backup'
New X configuration file written to '/home/xan/xorg.conf'

```
=> After stop and restart gdm, it still gives me the same result.

Here is my xorg.conf:

```

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
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
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

I don't see what I could do to find an solution... :|

Ok below is a copy of my xorg.conf file, take a lookL
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 191TFT"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 85.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1400x1050@60" "1024x768@75" "1600x1200@65" "1024x768@85" "1600x1200@60" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024@60 +0+0; 1280x1024@75 +0+0; 1280x960@60 +0+0; 1152x864@75 +0+0; 1024x768@60 +0+0; 1280x960@75 +0+0; 1024x768@70 +0+0; 1024x768@75 +0+0; 1024x768@85 +0+0; 832x624@75 +0+0; 800x600@60 +0+0; 800x600@85 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 800x600@56 +0+0; 640x480@85 +0+0; 640x480@75 +0+0; 640x480@72 +0+0; 640x480@60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

I have the same drivers as you installed. As to why you get that message about the drivers, I do not know. Do you have a listing under System>Administration>Nvidia X-server Settings. I believe that I am running the nvidia-envy set of drivers but it looks like I am running Nvidia's set--I think, I may not be reading this correctly. But my set of drivers matches exactly what you say that you have: 173.14.12

I am perplexed. May need one of the experts on this forum to help out.

---

### Post by ppc_guy on 2008-08-16
Just a suggestion that might help you guys out. Being I just configured my dual screen setup here.
With the newer Nvidia cards do this first:

@ the command line: apt-get install nvidia-glx-new
                    apt-get install nvidia-settings

After the driver installs run nvidia-settings as root to configure and save your settings. That's really all there is to it. Works like a dream here.

Nathan

---

### Post by RedRat on 2008-08-16
> **ppc_guy said:**
> Just a suggestion that might help you guys out. Being I just configured my dual screen setup here.
With the newer Nvidia cards do this first:

@ the command line: apt-get install nvidia-glx-new
                    apt-get install nvidia-settings

After the driver installs run nvidia-settings as root to configure and save your settings. That's really all there is to it. Works like a dream here.

Nathan

Well that is what I had done. I installed the nvidia drivers using envy. Is there a difference between nvidia-glx-new, nvidia-envy, and nvidia-proprietary? I am assuming that when I ran Envy, I got nvidia-envy driver, perhaps there is no difference between nvidia-envy and nvidia-glx-new. 

In any case as long as I set the driver to 60Hz refresh in Nvidia-Settings, I have no problems in Firefox, any higher and I got troubles. Since everything is working ok, not going to change anything--if it ain't broke, don't fix approach.

---

### Post by Xan63 on 2008-08-17
Hi,

I've got some good news:

After removing my compiz-fusion packages, I managed to install nvidia drivers 173.14.12! God bless Envyng! :D

I've still some problems: even after doing nvidia-xconfig & reboot, I can't access to Nvidia-settings.

And I don't see either the nvidia drivers, either my wireless drivers in the restricted drivers manager.(but no problem with wireless:) )

---

### Post by pwnprog on 2008-08-20
oh gosh... hate to de-rail, but am i supposed to be using gksudo to open nvidia settings? i've definitely used sudo a whole bunch of times to open it.

how long do i have until my roof implodes???

---

### Post by MrHippocampus on 2008-08-20
gksudo just gives you a nice pop up box to type in your password rather than having to type it in the terminal window. Other than that there isn't really any difference.

---

### Post by wd5gnr on 2008-08-21
Well, it isn't just the pop up box. The graphical sudo's also usually set up your configuration to use the right files. If you don't do that, some of your configs and all wind up getting set to root which will mess you up later. Usually, if I remember correctly, doing a su - will set "the right" environment but then you can't run X programs.

Read more: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)  (not my page, just a quick google result).

You might consider doing:

find ~ -user root -print

To see if you have any files you didn't expect to be owned by root in your home directory.

---

### Post by KindredCharles on 2008-08-21
> **pwnprog said:**
> oh gosh... hate to de-rail, but am i supposed to be using gksudo to open nvidia settings? i've definitely used sudo a whole bunch of times to open it.

how long do i have until my roof implodes???

I've always used sudo nvidia-settings to open gfx controls running twin view on my 7.10 gusty computer, no problems doing it this way for 6+ months.

---

### Post by MrHippocampus on 2008-08-21
> Well, it isn't just the pop up box. The graphical sudo's also usually set up your configuration to use the right files. If you don't do that, some of your configs and all wind up getting set to root which will mess you up later. Usually, if I remember correctly, doing a su - will set "the right" environment but then you can't run X programs.
Ubuntu now does some of this for the command line sudo in the same way the graphical one does so there isn't that much of a difference, this isn't the case on most other distros though where sudo just gives you root powers and doesn't change anything else.

For this case though all that's needed is the X display environment variable set for nvidia-settings to work properly as root, which sudo,su,gksudo and gksu all do nicely :)

---

### Post by mxcrowe on 2008-08-31
I have had similar problems with the Nividia X Server Settings.  I set the monitor the way I want it (1280x1024x75hz) and save the xorg.conf file.  Yes, I invoked the app via sudo, gksudo, etc.  I have checked teh xorg.conf file, and it seems to have the right settings.  Everything looks fine until I reboot.  At the login screen, the refresh rate looks fine, but after I login and the desktop starts, it changes the refresh back to 60Hz.  This is extremely annoying!!  Any ideas how to make these settings stay in place??

---

### Post by zippy_uk_2001 on 2008-11-13
Quick update - upgrading to Inrepid got me back to 3d graphics again - the hardware / graphics setting are a bit more detailed.

Too scared to try the dual monitors again though for now ...just in case :-)

---

### Post by loomsen on 2008-11-14
> **mxcrowe said:**
> I have had similar problems with the Nividia X Server Settings.  I set the monitor the way I want it (1280x1024x75hz) and save the xorg.conf file.  Yes, I invoked the app via sudo, gksudo, etc.  I have checked teh xorg.conf file, and it seems to have the right settings.  Everything looks fine until I reboot.  At the login screen, the refresh rate looks fine, but after I login and the desktop starts, it changes the refresh back to 60Hz.  This is extremely annoying!!  Any ideas how to make these settings stay in place??

Yep, even better:
[quote=me]I wouldn't want to risk a corrupt filesystem just cause if some sudoin around here and there.

You're aware of the difference between su, sudo, gksu and gksudo?

Usually, there is hardly any difference. Except of exactly such moves. I wouldn't recommend it. 

You could as well save it to your home folder for instance, drop yourself to a shell, and do this:

killall gdm
sudo -i
cp ~/xorg.conf /etc/X11/xorg.conf
exit
startx

1 line of sudoing, only 1 simple command you need to be root for. So, why risking sooo much? 
That really made me feel somewhat sick now 

Plz guys, plz, stop messing with sudo.
[/quote]
[from this thread](http://ubuntuforums.org/showthread.php?p=6074730#post6074730)

Further, for settings like digital-vibrance, anti-aliasing, antisoptric filtering, overclocking and stuff like this open nvidia-settings, as your user, no root no graphical su nothing, simply you.
Specify your desired settings, and do this
[[img]http://www.ubuntu-pics.de/thumb/5633/screenshot_01_mDyGsR.png[/img]](http://www.ubuntu-pics.de/bild/5633/screenshot_01_mDyGsR.png)

Then add a new starter to your preferences sessions, and use this command:
```

nvidia-settings -l

```

This will load your settings at startup then without opening up the GUI.

---

### Post by AaronP_ on 2008-11-14
> **KindredCharles said:**
> I've always used sudo nvidia-settings to open gfx controls running twin view on my 7.10 gusty computer, no problems doing it this way for 6+ months.
I've been talking to Alberto about how to tie nvidia-settings into PolicyKit.  I put together a PPA build that you might want to try out:
[https://launchpad.net/~aplattner/+archive](https://launchpad.net/~aplattner/+archive)

With this, it should pop up a PolicyKit authorization dialog instead of just failing when you try to save to /etc/X11/xorg.conf.

Note that it installs a setuid root helper program, so you may want to take that into consideration before trying it.

---

