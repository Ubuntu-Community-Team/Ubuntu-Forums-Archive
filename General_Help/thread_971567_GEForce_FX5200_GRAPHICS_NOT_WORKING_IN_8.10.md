---
title: "GEForce FX5200 GRAPHICS NOT WORKING IN 8.10"
date: 2008-11-05
forum: General Help
---

### Post by Rodhill on 2008-11-05
Well I've just updated to 8.10 from 8.04. I'm using a GEForce FX5200 graphics card and it won't work:confused:.
The PC just starts in low graphics mode all the time. I've tried to install from Hardware Drivers but it doesn't find any. I've looked in Synaptic Package manager and although the driver 173 is installed still nothing I've tried 177 too.
Everything was fine in 8.04.
Can anyone help me? If you know a command line please would you type it exactly how it's to be put in the terminal thanks.
Or do I wait for a fix to be sent as an update?

Thanks

Rod (PS I'm a nooby)

---

### Post by hcaleman on 2008-11-05
Have you tried doing it with envy-NG?  I have the same (crappy) card and had issues with the driver never working with Hardy.  Installed Envy and let it handle the video card driver and all is fine now.

---

### Post by CnlPepper on 2008-11-05
There is currently no nvidia legacy card driver in 8.10 (Intrepid) as nvidia had not released it when intrepid was provided for download. It should be available shortly (days to a few weeks) and should be provided in a system update. This was reported as a known issue with intrepid and was stated in the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

see: "Upgrading: nVidia "legacy" video support"

---

### Post by stinger30au on 2008-11-05
there is a *TON* of nvidia cards not working, this post i made earlier my interest you

[http://ubuntuforums.org/showthread.php?t=970237](http://ubuntuforums.org/showthread.php?t=970237)

---

### Post by Rodhill on 2008-11-05
> **hcaleman said:**
> Have you tried doing it with envy-NG?  I have the same (crappy) card and had issues with the driver never working with Hardy.  Installed Envy and let it handle the video card driver and all is fine now.

I'll try that - many thanks. I can't believe this release would be issued with these problems. The card worked fine before and did everything fine. I'm not a gamer or need a top graphics card :confused:

---

### Post by fragos on 2008-11-05
My FX5200 works after the upgrade. Run System-> Administration-> Hardware Drivers. You need to hit the activate button.

---

### Post by Rodhill on 2008-11-06
> **fragos said:**
> My FX5200 works after the upgrade. Run System-> Administration-> Hardware Drivers. You need to hit the activate button.
I've tried that and it won't activate.

Rod

---

### Post by Rodhill on 2008-11-06
> **hcaleman said:**
> Have you tried doing it with envy-NG?  I have the same (crappy) card and had issues with the driver never working with Hardy.  Installed Envy and let it handle the video card driver and all is fine now.

There is a choice of 3 Envy NG's which one do I choose?

Rod

---

### Post by Yellow Pasque on 2008-11-06
> **Rodhill said:**
> There is a choice of 3 Envy NG's which one do I choose?

Rod
Install envyng-core if you're using (X)Ubuntu or envyng-qt if you're using Kubuntu/KDE.

---

### Post by Peter09 on 2008-11-06
Hi,
I'm not sure that envy-ng is actually working in Intrepid. During development I tried and it did not.

Two things to check.

1. There is no driver waiting to  be enabled in System->Administration->Hardware Drivers

2. Booting into recovery mode and doing an xfix  may resolve it. (Check 1. after doing it as well)

also post the output of

```
lshw -C display
```

---

### Post by TeXtonyx on 2008-11-06
Well, I fixed something like this recently in 8.04
I don't know if it will work for you in 8.10

I used the search option in Synaptic and entered "envy".
Then I marked envy-core and envyng-gtk(gnome I think) for install.

It took 3 or 4 minutes. The other thing is that I had saved a
working xorg.conf from another install. Did you save your xorg.conf
from your 8.04 install which worked. My card is a geforce fx 5500
(dual screen) and I needed the working xorg.conf, not the fresh
xorg.conf that comes with a new install which isn't configured
for your card. If your card is for 3D, maybe the release notes
re: when nvidia will release a legacy driver for 8.10 apply to you.
Maybe you have an xorg.conf.bak or similar in /etc/X11, look about.

---

### Post by Rodhill on 2008-11-06
> **Peter09 said:**
> Hi,
I'm not sure that envy-ng is actually working in Intrepid. During development I tried and it did not.

Two things to check.

1. There is no driver waiting to  be enabled in System->Administration->Hardware Drivers

2. Booting into recovery mode and doing an xfix  may resolve it. (Check 1. after doing it as well)

also post the output of

```
lshw -C display
```

Hi Peter,
I've checked for hardware drivers none there. Can you tell me what to do exactly in 2 (xfix) above as I'll try that.

Rod

---

### Post by Peter09 on 2008-11-06
Hi,
can you post the output of

```
ldhw -C display
```
For xfix.

Got to recovery mode by hitting escape at the Grub prompt. This will give you a list of options. Go down to the second one which is normally recovery mode and hit enter. When you get the menu choose xfix.

Afterward check there is no driver waiting to be enabled in System->Administration->Hardware Drivers

---

### Post by seps1816 on 2008-11-06
> **Rodhill said:**
> There is a choice of 3 Envy NG's which one do I choose?

Rod

Hey Rod Im having the same problem let me know if using Envy works for you cause i might just wait for the drivers to be updated but i'd like to get the card going asap 
Thanks 
seps1816

---

### Post by sharkster2007 on 2008-11-06
I had similar problems installing & enabling my Nvidia 6600GT I have a manual .deb file download solution and Greyarea2 seemed to get the automatic update version working.

My thread is [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038) (also contains a thread link to Greyarea2's Post)

Hope this helps solve your problem :-)

---

### Post by Spades_Neil on 2008-11-06
God, it looks like the 8.10 update breaks everything with graphics it seems.

I've completely ruined my computer ever since the update. I'm using a 7.10 install disk to help recover my files and transfer them to a flash drive, and move it to another computer.

---

### Post by fragos on 2008-11-06
Problems may relate to what non-Ubuntu stuff you installed paticularly if some of it was compiled. Upgrades can only be made to things installed as a deb package intended for the distro and release you were running. Compiling Nvidia drivers is one of those time you're asking for trouble at the next release. In the past Envy compiled Nvidia drivers for you -- I don't know about now. If an upgrade didn't work a clean install probably will.

---

### Post by seps1816 on 2008-11-06
i did a clean install a got the ame issue with a geforce fx 5200 card still not working if there is a deb package can someone post a link

---

### Post by seps1816 on 2008-11-06
> **sharkster2007 said:**
> I had similar problems installing & enabling my Nvidia 6600GT I have a manual .deb file download solution and Greyarea2 seemed to get the automatic update version working.

My thread is [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038) (also contains a thread link to Greyarea2's Post)

Hope this helps solve your problem :-)

would u happen to know which driver i should downlaod for a geforce fx 5200 from that link? would be a big help

---

### Post by Rodhill on 2008-11-07
> **seps1816 said:**
> Hey Rod Im having the same problem let me know if using Envy works for you cause i might just wait for the drivers to be updated but i'd like to get the card going asap 
Thanks 
seps1816

I installed Envy but I really don't know what to do to use it. I'm scared I won't get any graphics if I use the terminal incorrectly.Rather leave it alone for now. I'm ok if someone can show me what to type in.
I'm fairly new at this Linux, & whilst I love the system it scares the **** out of me sometimes. I wished I'd not done this upgrade now.
It might be an idea to leave it in low graphics mode and wait for a new driver for 8.10:confused:

Rod

---

### Post by seps1816 on 2008-11-07
> **Rodhill said:**
> I installed Envy but I really don't know what to do to use it. I'm scared I won't get any graphics if I use the terminal incorrectly.Rather leave it alone for now. I'm ok if someone can show me what to type in.
I'm fairly new at this Linux, & whilst I love the system it scares the **** out of me sometimes. I wished I'd not done this upgrade now.
It might be an idea to leave it in low graphics mode and wait for a new driver for 8.10:confused:

Rod

I tried it out a second time and installed the envy drivers nothing worked so im just redoning the system and waiting till the new drivers come out im on the same boat as u rod i bought this card the other night and now im kinda regretting it hopefully this problem gets fixed soon 

seps1816

---

### Post by Rodhill on 2008-11-10
Well it appears some drivers have appeared on the last update. I've downloaded them (173 & 96) but neither will activate:confused:
Should this be working now? If I check Nvidia x server settings it just says I don't appear to be using NVidia drivers and to edit my x configeration file? So how is that done?

Rod

---

### Post by fragos on 2008-11-10
My FX5200 works just fine with the Ubuntu supplied drivers. What you may have done is installed drivers that aren't visible to the package management system. If you compiled them yourself for example that will be the case. 1st thing to do run Synaptic to install "nvidia-glx-173" to insure the proper driver is available.

Editing /ect/X11/xorg.conf might work. It's owned by root so i suggest you type <Alt>F2 to get a "Run application" window. Enter "gksudo gedit /etc/X11/xorg.conf". Scan down the file looking for

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Note your driver line may be set differently. If its "nvidia", change it to "nv" and if it's anything else change it to "nvidia". Regadless of what the GUI tells you this is what determines which video driver is loaded.

---

### Post by Rodhill on 2008-11-11
Hi Fragos,
Many thanks for the information I downloaded the diver & did what you said and it says this:-

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Is this right?
Right the driver shows up in 'Hardware Drivers' but when I try to activate it the window opens with the blue box going back and forward and suddenly stops and won't install??
When I check my 'Nvidia X server settings', a box shows there's no configeration, saying this
'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server'. 
This is the bit I can't understand in what I should do. I think this is the main problem. Can you tell me what to type in the terminal to do this?

Sorry but I'm new to this and it is taking a bit to get my head round it:(

Rod

---

### Post by stinger30au on 2008-11-11
> **Spades_Neil said:**
> God, it looks like the 8.10 update breaks everything with graphics it seems.

I've completely ruined my computer ever since the update. I'm using a 7.10 install disk to help recover my files and transfer them to a flash drive, and move it to another computer.


hence why it is a marvellous idea to backup all data *before* upgrades

---

### Post by fragos on 2008-11-11
> **Rodhill said:**
> Hi Fragos,
Many thanks for the information I downloaded the diver & did what you said and it says this:-

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Is this right?
Right the driver shows up in 'Hardware Drivers' but when I try to activate it the window opens with the blue box going back and forward and suddenly stops and won't install??
When I check my 'Nvidia X server settings', a box shows there's no configeration, saying this
'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server'. 
This is the bit I can't understand in what I should do. I think this is the main problem. Can you tell me what to type in the terminal to do this?

Sorry but I'm new to this and it is taking a bit to get my head round it:(

Rod

My screen section is different:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

My best guess is to delete the line that isn't in mine.

---

### Post by seps1816 on 2008-11-18
Hey Fargos just want to start with thanks for taking the time and posting a solution up, but I have followed your driections and still the system wont load right. I even changed the "nvidia" part to "nv" nothing worked I'd really like to get this card to work but if worse comes to worse i'll find some other use for it and just get a new card with better suppor. What do u think?

---

### Post by fragos on 2008-11-18
> **seps1816 said:**
> Hey Fargos just want to start with thanks for taking the time and posting a solution up, but I have followed your driections and still the system wont load right. I even changed the "nvidia" part to "nv" nothing worked I'd really like to get this card to work but if worse comes to worse i'll find some other use for it and just get a new card with better suppor. What do u think?

I've run out of suggestions. My FX5200 has always worked well with Ubuntu releases. There has to be something about how your system is configured that's different from mine. I always use the driver selected by Ubuntu and stay away from the likes of Envy, Automatrix or compiling myself. If your system won't work with the FX5200 it may not work with other Nvidia cards. I suggest a clean new install letting Ubuntu do the heavy lifting on selecting drivers.

---

### Post by Terry of Astoria on 2008-11-20
I have just now got my graphics going in hi res. on my Geforce FX 5200 AGP card. I used some program months ago to configure 8.04 but I can't remember it . . . Anyway today I activated the nvidia driver #173 in the "restricted drivers" manager and then rebooted, but that didn't do the trick. I was still stuck in ol' 640x480. I replaced xorg.conf with my old xorg.conf that was created by that unremembered program. That did it. Now it's pretty and I do have 3d but I'll have to test how good it is . . .
   Here is my xorg.conf . . . you can try using it, or part of it. I remember I had the hardest time getting my fx 5200 to work the first time. This time I'm documenting it here.

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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E196FP"
	Horizsync	31.0-83.0
	Vertrefresh	56.0-76.0
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by fragos on 2008-11-20
FYI: the following is the system generated /etc/X11/xorg.conf that works with my FX5200 and Ubuntu 8.10:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

---

### Post by sharkster2007 on 2008-11-23
Sorry seps1816

I'd install the 177 Driver (recommended) personally. don't know which one you need for GEForce FX5200, though One of the Nvidia .deb files listed contains a list of cards i will work with in Synaptic before you install it is listed on the description after you double click the .deb file.

Its the one that begins [COLOR="SeaGreen"]nvidia-glx[/COLOR]

Hope this helps

---

### Post by kulisek on 2008-11-26
Although, I have not yet figured out how to get the 3d effects to work, because of issues with NVIDIA driver, I think that after I "disassemble" the contents of the xorg.conf that you have kindly posted, I just may learn something and get to the bottom of my video card issues.
Out of the box, on clean install of Ubuntu 8.10, the resolution is fine, the only thing that I still have not been able to try is the 3d effects. So in the end it is not that big of a deal, whether I get the 3d working or not, it's purely something to tinker around with. Thank you.

---

### Post by kulisek on 2008-11-26
Finally I have managed to get the 3D effects to work and make use of my GEForce FX5200. 


Here is what I have for my xorg.conf

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"NEC"
	Modelname	"FE771SB"
	Horizsync	30.0-70.0
	Vertrefresh	50.0-120.0

  modeline  "1280x1024@60" 109.62 1280 1336 1472 1720   1024 1024 1026 1062+hsync +vsync
  
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

As you can tell, I have pretty much took only what I needed from your (Terry of Astoria) xorg.conf that you have posted. I changed my monitor model and type accordingly. The next thing that I needed was at least one modline for the time being. For that I had to figure out what my monitor's specs were and that I accomplished by searching on google for my monitor's specs as I don't have the manual on hand. 
Once I had the Horizontal and Vertical Syncs and the Refresh Rate values, I created my modline using 

[http://bohne-lanng.de/spec/linux/modeline/]("http://bohne-lanng.de/spec/linux/modeline/") tool.

Placed the modline in my xorg.conf and bingo.

Thanks again Terry of Astoria

---

### Post by Sam Lars on 2008-12-07
I'm having issues getting an FX5200 to work also.  I'm pretty sure it was just using the Ubuntu drivers before the upgrade, and as soon as it rebooted, the graphics died.
The Xorg log is saying that it can't find the kernel modules.  I have the kernel modules packages installed and it still refuses to work.  I also tried installing the latest driver from Nvidia, but it couldn't find the source, and when I specified the source location, it errored out.
I noticed one of the people that had it working had an AGP card... mine's PCI, maybe that could be part of why some people don't have problems?

---

### Post by Sam Lars on 2008-12-09
I ended up using envy-ng -t, and it worked great.

---

### Post by seps1816 on 2008-12-17
> **Sam Lars said:**
> I ended up using envy-ng -t, and it worked great.

Hey sam I have PCI FX5200 card and its been doing basically what u explained in the post before everytime i install the driver and restart it doesnt load graphics just the text interface so i stop trying to mess with it cause i would have to reinstall ubuntu to get everything working again since i dont really know much about messing with xorg if u could help me to get this working it would be a big help. 
Thanks for your time

---

### Post by Sam Lars on 2008-12-17
Well when I rebooted and ended up with the text interface, I did Alt+F1 to log in to there, and then I ran
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After that, you can do 
```
startx
```
to get back into X or you can restart (sudo reboot).

As for Envy, I installed envy-ng.  You can find it in Synaptic or by doing
```
sudo aptitude install envy-ng
```
After that, I ran
```
sudo envy-ng -t
```
(I'm pretty sure it needed sudo) and followed the prompts to install the Nvidia driver.
I don't remember if this is exactly what I did, and I'm not on Linux right now, so post back if you have any questions.

---

### Post by Rodhill on 2008-12-26
Well I gave up in the end. I got a GEForce FX6200. Soon as I put it in it worked fine and downloaded the driver. Happy bunny now. Thanks though for all the replies and help.

---

