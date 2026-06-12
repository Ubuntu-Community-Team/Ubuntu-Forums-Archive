---
title: "Resolution problem with external monitor on intel 915"
date: 2008-12-26
forum: Hardware
---

### Post by nathanbosch on 2008-12-26
I am trying to setup my new 24" Samsung monitor as a second screen for my laptop.  I have a Toshiba Satellite M55-S135 with the Intel 915 on-board graphics.  My problem is that while the monitor is 1920x1200 I don't have that option in the screen resolution dialog.  Also of note, when I try to use the 1600x1200 option the Samsung monitor is very dark, more so at the bottom of the screen, and is unreadable.  I booted the latest Knoppix live DVD and I was able to set the external to 1920x1200 only after I reduced the resolution on the laptop screen (capable of 1280x786 but I had to reduce to 800x600) The Knoppix dialog said that I am limited to a virtual screen size of 1920x1920 so I was also forced to place the monitors vertically in the virtual screen instead of side by side.
	Knoppix boots with the 24" at full resolution with the laptop cloning the top left corner.  Compiz is enabled and the 3d rotating cube with transparency works fairly smoothly.  After changing the resolution to separate the monitors all effects including the cube still worked.
	Optimally I'd like to use both monitors at full resolution, although I'd be very happy running the laptop screen at 1280x700 and set up a 1920x1920 virtual screen size(but I'll admit I'm at a loss how I'd accomplish that).  I would not prefer it, but I'd settle for the 1920x1220, 800x600 combo that worked in Knoppix.  I don't need to be able to run Compiz or anything, but I do want all the real estate I can get as I find I'm much more productive when I can see a lot of code on the screen at once...
	After searching through some old forums I see that the old solution was to use 915resolution to add some resolution modes, but while trying to install it I found that it conflicts with xserver-xorg-video-intel which I have installed (and from what I can tell is currently the recommended solution)  I was going to try to compile 915resolution, but I read that the bios modes are not used anymore, so I figured it would be pointless. Currently, with the 24" running in a reduced widescreen resolution everything runs fine, and I have Compiz enabled with some of the 2d effects running just fine.  I've edited xorg.conf before so I'm somewhat familiar, but I haven't tried anything with this problem because I wouldn't know where to start.
	I am going on a trip for a few days, but if there are any suggestions I'll try them as soon as I get back, I'd like to get this problem solved before I go back to school for spring semester.  Also, if you need any more information about my hardware or installed software let me know and I'll post it when I'm back.

Thanks a ton for any help!


Here is some output that may be relevant:

On my Intrepid Install running Gnome:

nathan@goofy:~$ lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

nathan@goofy:~/tmp$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

nathan@goofy:~/tmp$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 1668, maximum 1600 x 1792
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1600x1200      60.0     60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       59.9* 
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1280x768+0+900 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

On a Knoppix boot running KDE:

knoppix@Knoppix:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

knoppix@Knoppix:~$ xrandr --output LVDS --mode 800x600 --below VGA
knoppix@Knoppix:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1800, maximum 1920 x 1920
VGA connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+   60.0
   1600x1200      59.9
   1680x1050      60.1
   1400x1050      72.0     60.0
   1280x1024      59.9
   1280x960       72.0     59.9
   1152x864       75.0     74.8     60.0
   1024x768       70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   768x576        75.0     72.0     60.0
   640x480        75.0     72.8     66.7     60.0     63.1
   720x400        70.1
LVDS connected 800x600+0+1200 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0 +   60.0
   1024x768       60.0
   800x600        60.3*
   640x480        59.9
TV disconnected (normal left inverted right x axis y axis)

---

### Post by eyik66 on 2009-01-07
this is off topic, but I could really use your help. My screen is out (same computer), and my fn+f5 key isn't working. Can you direct me to the "output to monitor" that you can do after right clicking on the desktop with your mouse? If you could say: right click, arrow down 5 spaces, arrrow over 1, arrow down 3, hit enter. That would be great. Thanks a million if you can,

---

### Post by nathanbosch on 2009-01-21
> **eyik66 said:**
> this is off topic, but I could really use your help. My screen is out (same computer), and my fn+f5 key isn't working. Can you direct me to the "output to monitor" that you can do after right clicking on the desktop with your mouse? If you could say: right click, arrow down 5 spaces, arrrow over 1, arrow down 3, hit enter. That would be great. Thanks a million if you can,
Well in my install 8.10 there is not screen resolution option in the right click menu, sorry.  Have you tried booting with the external monitor plugged in an on?  If you have the settings to factory default in the bios it should choose to use that display instead of the laptop display.  Also, if you can get it up and on the network and you can ssh in form another box you can use xrandr to change the screen resolution options from the comamand line.  Good luck!

---

### Post by nathanbosch on 2009-01-21
Well I'm a little embarassed to say this was a very easy fix.  After I finally got around to changing settings in the xorg.conf file I found the 1 line solution.  In my virtual display I simply set the resolution to 3200 1200... wide enough for the 1280 and 1920 monitors to be placed side by side... after a restart of X the correct options were available in the GUI screen resolution dialog as well as appropriate output from xrandr... for reference here is the relevant clip from xorg.conf and the new xrandr output.

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3200 1200
	EndSubSection
EndSection

```

```
:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 3200 x 1200
VGA connected 1920x1200+1280+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0     60.0  
   1680x1050      60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       59.9  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1280x768+0+432 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```

---

### Post by nathanbosch on 2009-01-21
After playing around with it I found that while compiz effects wouldn't work in 3200x1200 they seem to work ok if I place the monitors on top of eachother in the virtual display and use a resolution of 1920x1968, so anyone with similar issues might try different orientations in case one works smoother than the other.

---

### Post by starwed on 2009-06-30
I found an explanation of this problem here: [Dual monitor with desktop effects in 8.10](http://codebaboon.com/taxonomy/term/45).

---

