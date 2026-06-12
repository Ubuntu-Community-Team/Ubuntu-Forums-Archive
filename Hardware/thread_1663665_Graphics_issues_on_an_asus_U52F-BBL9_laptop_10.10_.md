---
title: "Graphics issues on an asus U52F-BBL9 laptop 10.10 64 bit"
date: 2011-01-09
forum: Hardware
---

### Post by felixtheratruns on 2011-01-09
Card:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1c22
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at e080 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915


joel@joel-U52F-BBL9:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:e080(size=8)

```Problem1: I cannot change to a higher resolution. xrandr also adds modes to DP1 and not the active LVDS1
```
joel@joel-U52F-BBL9:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
joel@joel-U52F-BBL9:~$ xrandr | grep maximum
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
joel@joel-U52F-BBL9:~$ cvt 1600 1200
# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
joel@joel-U52F-BBL9:~$ xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
joel@joel-U52F-BBL9:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
  1600x1200_60.00 (0xcb)  161.0MHz
        h: width  1600 start 1712 end 1880 total 2160 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1207 total 1245           clock   59.9Hz
joel@joel-U52F-BBL9:~$ xrandr --addmode LVDS1 1600x1200_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
joel@joel-U52F-BBL9:~$ xrandr --addmode DP1 1600x1200_60.00

```When I run "xrandr --output DP1 --mode 1600x1200_60.00" it gives me a black screen.

Problem 2: When I stop the xserver with "sudo service gdm stop" I do not get a counsel. I also notice that I do not have a xorg.conf file (at least not anywhere in /etc/X11/). These are the relevant errors when I stop the gdm:
```
init: Failed to open system counsel: Input/output error
```Thanks.

---

### Post by gregb49 on 2011-01-10
I don't have a solution, just a similar problem. Why I can get 1024X768 using MEPIS, Puppy, 8:04 but not 10:10 I don't know. Yes, there is no xorg.conf file. If I create one, it vanishes. If I amend xorg.conf.failsafe, my amendments get removed on reboot. I think I'm on day 4 of trying to resolve this and getting no where. What happened to the old ```
dpkg-reconfigure xserver-xorg
```At least that allowed you to play with various settings. My xrandr info tells me even less than yours> ubuntu@ubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 400 x 300, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
and I did try > ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768  771
ubuntu@ubuntu:~$: command not found


[SIZE="1"]P4 with Matrox G450 AGP[/SIZE]

---

### Post by felixtheratruns on 2011-01-10
dpkg-reconfigure xserver-xorg

Ge[FONT=monospace]ts rid of the "init" error when I do "sudo service gdm stop" however nothing else changes, it still does not give me a counsel. 

I forgot to mention I have another problem where after closing my laptop and opening it I do not get the xserver or a counsel and need to turn it off completely and boot up before I can do anything. Thanks though.





[/FONT]

---

### Post by felixtheratruns on 2011-01-10
Did not let me do anything new xrandr either. Still freezes and doesn't let me do anything when I change the output.

---

### Post by gregb49 on 2011-01-10
> **felixtheratruns said:**
> Did not let me do anything new xrandr either. I have made some progress but can probably only claim the prize for the most inelegant solution ever. I've carried out the following:

[LIST=1]
[*]In the folder /usr/share/X11/xorg.conf.d/ I've created a file called > 10-monitor.conf containing just the monitor and card info from a working xorg.conf file, in my case, from puppy 5.11. I did try the whole xorg.conf file, but ended up with no keyboard or mouse.
[*]Starting the Ubuntu 10.10 in recovery mode, when at the prompt, I type ```
startx -- -dpi 100
```and now have something like a 1024x768 display.
[/LIST]

I hope this horrible solution gives some clues to someone with a Matrox G450 or other xorg problems, as to how to arrive at a much better solution.

I want OpenOffice 3.2; Zim, GFTP, Kompozer, Gimp, Chrome and Dropbox all on one desktop. If I didn't need all those together, I would have discarded Ubuntu 10.10's treatment of this graphics card, a little while ago and stuck with 8.04, Puppy or Mepis, none of which give the whole solution that I want.

---

### Post by felixtheratruns on 2011-01-28
I'm in school so I still haven't had time to try your solution yet :( However, could you post your
10-monitor.conf and xorg.conf files? I know I probably have different hardware but it might give me an idea if something screws up when I do have time to install and dual boot puppy 5.11

---

### Post by felixtheratruns on 2011-01-29
I feel like the biggest moron on the face of the planet. I have probably spent 20 hours total trying to add a higher resolution. I do not think our problems are the same now.

The reason I cannot get higher than 1366x768 is because the asus U52F-BBL9 laptop does not support a higher resolution: [http://www.bbspot.com/reviews/asus-u52f-bbl9-laptop-with-an-intel-core-i5-processor](http://www.bbspot.com/reviews/asus-u52f-bbl9-laptop-with-an-intel-core-i5-processor)
[:lolflag:]("http://www.bbspot.com/reviews/asus-u52f-bbl9-laptop-with-an-intel-core-i5-processor:lolflag:")

This has nothing to do with ubuntu or software or drivers. I'm just used to higher resolutions on other laptops so this low resolution felt strange and I assumed that it couldn't be the maximum setting.

Lesson: make sure your base assumptions are correct before you start the quest for the holy grail.

Update: I marked this thread as SOLVED, however I undid that because I  still do have problems with the fact that stopping the xserver freezes  my machine and that I cannot hibernate or suspend because of that. (at one point I did have it working though) I will  work on this next weekend and come up with a solution (using the vast  knowedge aquired from my quest for the holy grail)

---

### Post by gregb49 on 2011-01-30
> **felixtheratruns said:**
> I feel like the biggest moron on the face of the planet. I have probably spent 20 hours total trying to add a higher resolution...and neither have I resolved my problem. I thought I had because I had managed to get a desktop back, that is bringing the icons and panels back onto the screen hence my thinking that I had achieved the 1024 resolution. I'm still stuck at 800x600. 

My question remains. If my graphics card gives 1024 with 8.04, puppy linux and Mepis 8, why is it such a struggle with 10:10? I've download the Matrox drivers which have an xserver folder containing folders number like 7.0.0 and files such as mga_hal_drv.so but haven't a clue what to do with them.
For info, the 10-monitor.conf is shown below. I've emailed the larger xorg.conf file. All the best with the quest
```
Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Device"
    Identifier    "Device0"
    Driver        "vesa" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier    "Screen0"  #Collapse Monitor and Device section to Screen section
    Device        "Device0"
    Monitor       "Monitor0"
    DefaultDepth  16 #Choose the depth (16||24)
    SubSection "Display"
        Depth     16
        Modes     "1024x768_75.00" #Choose the resolution
    EndSubSection
EndSection

```

---

### Post by felixtheratruns on 2011-01-30
[U]removed because subject line was wrong
[/U][]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

---

### Post by felixtheratruns on 2011-01-30
One thing to check. Make sure you are actually getting a higher  resolution on puppy (this confused me too). Puppy can set the resolution  in the xorg.conf file to something higher, but if the monitor doesn't  support it, during the monitor test it will only have a lower  resolution. Also puppy linux looks smaller with the icons and everything  at the same resolution. (which confused me also) but then again 800x600  sounds like a very low max res for any monitor, probably a driver  issue.

Have you looked at the graphics drivers? Also there are some weird  workarounds for some cards, like this (I know it isn't the same problem  but it still might be useful):
[http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

---

### Post by gregb49 on 2011-02-04
> **felixtheratruns said:**
> Have you looked at the graphics drivers?I've no idea how to change those, but I'll look for a 'Howto'. I've downloaded new drivers, but the files make no sense to me> 
[http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")I've tried the ```
xforcevesa
``` suggestion but am still only offered 800x600 or 640x480 options when in Ubuntu/system/preferences/monitor

---

### Post by gregb49 on 2011-02-04
I'm now on my 20+ version of 10-monitor.conf and have made some progress. I can have 
[LIST=1]
[*]800x600 plus mouse, keyboard and sound
[*]1024x768 plus mouse no keyboard no sound
[*]1024x768 no mouse no keyboard no sound
[/LIST]

Here is the basic 10-monitor.conf file that I am working on now```

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Enables mode switching with xrandr
# There is a report that this can cause Xorg not to work on some
# video hardware, so default is commented-out...
# but i want to use it in xorgwizard so leave on...

    Option "RandR" "on"

# With this, Xorg won't talk to HAL to add evdev devices and you'll be back
# with the old Xorg behavior (pre-7.4)...

   Option "AutoAddDevices" "false"

# For no-Hal, kirk also suggests this...

#    Option "AllowMouseOpenFail" "true"

# Xorg 7.4, Ubuntu Jaunty, CTRL-ALT-BACKSPACE is disabled by default...

    Option "DontZap" "false"

EndSection



#everything past here is auto-generated by Puppy's Xorg Wizard...

#everything past here is auto-generated by Puppy's Xorg Wizard...


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "pc102"
	Option      "XkbLayout" "gb" #xkeymap0
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2" #mouse0protocol
	Option	    "Device" "/dev/mouse"
	#Option      "Emulate3Buttons"
	#Option      "Emulate3Timeout" "50"
	Option      "ZAxisMapping" "4 5" #scrollwheel
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-48.5
	VertRefresh  40-70
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1024x768"
	EndSection
	
Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "SWcursor"           	# [<bool>]
	#Option     "HWcursor"           	# [<bool>]
	#Option     "PciRetry"           	# [<bool>]
	#Option     "SyncOnGreen"        	# [<bool>]
	#Option     "NoAccel"            	# [<bool>]
	#Option     "ShowCache"          	# [<bool>]
	#Option     "MGASDRAM"           	# [<bool>]
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "UseFBDev"           	# [<bool>]
	#Option     "ColorKey"           	# <i>
	#Option     "SetMclk"            	# <freq>
	#Option     "OverclockMem"       	# [<bool>]
	#Option     "VideoKey"           	# <i>
	#Option     "Rotate"             	# [<str>]
	#Option     "TexturedVideo"      	# [<bool>]
	#Option     "Crtc2Half"          	# [<bool>]
	#Option     "Crtc2Ram"           	# <i>
	#Option     "Int10"              	# [<bool>]
	#Option     "AGPMode"            	# <i>
	#Option     "AGPSize"            	# <i>
	#Option     "DigitalScreen1"     	# [<bool>]
	#Option     "DigitalScreen2"     	# [<bool>]
	#Option     "TV"                 	# [<bool>]
	#Option     "TVStandard"         	# [<str>]
	#Option     "CableType"          	# [<str>]
	#Option     "NoHal"              	# [<bool>]
	#Option     "SwappedHead"        	# [<bool>]
	#Option     "DRI"                	# [<bool>]
	#Option     "MergedFB"           	# [<bool>]
	#Option     "Monitor2HSync"      	# [<str>]
	#Option     "Monitor2VRefresh"   	# [<str>]
	#Option     "Monitor2Position"   	# [<str>]
	#Option     "MetaModes"          	# [<str>]
	#Option     "OldDmaInit"         	# [<bool>]
	#Option     "ForcePciDma"        	# [<bool>]
	#Option     "AccelMethod"        	# [<str>]
	#Option     "KVM"                	# [<bool>]
	Identifier  "Card0"
	Driver      "mga" #card0driver
	VendorName  "Matrox Graphics, Inc."
	BoardName   "MGA G400/G450"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
	#Option         "metamodes" "1024x768_60 +0+0" #METAMODES_0
	Subsection "Display"
		Depth       16
		Modes       "1024x768"
	EndSubsection
EndSection

#PuppyHardwareProfile=Matrox_Graphics_Inc_

```The key appears to be the lines```
# With this, Xorg won't talk to HAL to add evdev devices and you'll be back
# with the old Xorg behavior (pre-7.4)...

   Option "AutoAddDevices" "false"


```If I comment out the option, I get 800x600 max plus mouse and keyboard. If I leave it in, as shown, I get 1024 but loose other vital devices, as follows:

[LIST=1]
[*]Leave Server section in. Looks like 1024 resolution but no keyboard, mouse or sound.
[*]Take server section out. 1024 resolution with mouse but no keyboard, or sound. If I log in through recovery consol, I can surf the web to my hearts content but with no keyboard, that is of very limited use.
[*]Take out various bits of the Server section. Results from crashing the computer, to command line only, but I cannot get 1024 resolution with keyboard and mouse.
[/LIST] 

I feel I'm almost there, but what step should I take next? I've tried installing Matrox G450 drivers but the install programme tells me that I'm using the wrong version of XServer.

---

### Post by gregb49 on 2011-02-04
Suddenly I have 1024x768 + kb, mouse and sound by using the following 10-monitor.conf file```


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-48.5
	VertRefresh  40-70
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1024x768"
	EndSection
	
Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "SWcursor"           	# [<bool>]
	#Option     "HWcursor"           	# [<bool>]
	#Option     "PciRetry"           	# [<bool>]
	#Option     "SyncOnGreen"        	# [<bool>]
	#Option     "NoAccel"            	# [<bool>]
	#Option     "ShowCache"          	# [<bool>]
	#Option     "MGASDRAM"           	# [<bool>]
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "UseFBDev"           	# [<bool>]
	#Option     "ColorKey"           	# <i>
	#Option     "SetMclk"            	# <freq>
	#Option     "OverclockMem"       	# [<bool>]
	#Option     "VideoKey"           	# <i>
	#Option     "Rotate"             	# [<str>]
	#Option     "TexturedVideo"      	# [<bool>]
	#Option     "Crtc2Half"          	# [<bool>]
	#Option     "Crtc2Ram"           	# <i>
	#Option     "Int10"              	# [<bool>]
	#Option     "AGPMode"            	# <i>
	#Option     "AGPSize"            	# <i>
	#Option     "DigitalScreen1"     	# [<bool>]
	#Option     "DigitalScreen2"     	# [<bool>]
	#Option     "TV"                 	# [<bool>]
	#Option     "TVStandard"         	# [<str>]
	#Option     "CableType"          	# [<str>]
	#Option     "NoHal"              	# [<bool>]
	#Option     "SwappedHead"        	# [<bool>]
	#Option     "DRI"                	# [<bool>]
	#Option     "MergedFB"           	# [<bool>]
	#Option     "Monitor2HSync"      	# [<str>]
	#Option     "Monitor2VRefresh"   	# [<str>]
	#Option     "Monitor2Position"   	# [<str>]
	#Option     "MetaModes"          	# [<str>]
	#Option     "OldDmaInit"         	# [<bool>]
	#Option     "ForcePciDma"        	# [<bool>]
	#Option     "AccelMethod"        	# [<str>]
	#Option     "KVM"                	# [<bool>]
	Identifier  "Card0"
	Driver      "mga" #card0driver
	VendorName  "Matrox Graphics, Inc."
	BoardName   "MGA G400/G450"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
	#Option         "metamodes" "1024x768_60 +0+0" #METAMODES_0
	Subsection "Display"
		Depth       16
		Modes       "1024x768"
	EndSubsection
EndSection

#PuppyHardwareProfile=Matrox_Graphics_Inc_
```In all the changes that I have made, I must have changed something else to enable this. The only two things I can think of are:
[LIST=1]
[*]Trying to install the matrox 2006 drivers using install.sh 
[*]Trying to install every Matrox component that I could find, through synaptic package manager.
[/LIST]
I can only hope that all this helps someone else, even though my steps to success are so badly documented.

My thanks to Felix for his help. I hope that he can solve the ASUS U52F issues.

---

### Post by felixtheratruns on 2011-02-04
Working a big project for school right now so haven't had time to look into this much more. But have you tried this? [http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)

Try using that, and just set your horizontal resolution to your monitor's max. I am using it on my laptop currently because I am not totally satisfied with the max resolution. (it is slightly blurry though because my LCD does not support above the max res of course)

---

