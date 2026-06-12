---
title: "Resolution Problem on Toshiba Laptop can't set resolution above 800x600"
date: 2009-02-11
forum: Hardware
---

### Post by Diamond1984 on 2009-02-11
800x600 is the highest resolution available under the resolution settings. this isn't big enough to use all the available space on the screen it leaves about and inch and a quarter on the side and an inch on the top.  I've tried going in through the command line and modifying the configuration file to allow for higher resolutions and something is overriding my changes.  The automatic detection for the resolution seems to be screwed up or not working with this laptop.  I have a Toshiba Satellite 
A24-S279 P4-2.80 15x512m 60 RW/DV WLg 

I'm new at modifying files within the command line. I had someone who was very well versed assist me over the phone but without being here in person he couldn't help me any further.  any detailed help would be greatly appreciated.

---

### Post by mikewhatever on 2009-02-11
Can you post the outputs of the following commands from Terminal:
sudo lshw -C display
xrandr -q

---

### Post by Diamond1984 on 2009-02-11
evangeline@evangeline-laptop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=8
evangeline@evangeline-laptop:~$ xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0

---

### Post by mikewhatever on 2009-02-11
It looks like your graphics hardware is not detected and the computer is probably running in the safe graphics mode. I've never heard of 'CyberBlade XPAi1' or Trident Microsystems, but apparently, there is a driver for it. What output do you get from 
<dpkg -s xserver-xorg-video-trident>?

---

### Post by roger_1960 on 2009-02-11
Hi

Have a look at this thread - solution is on third page!

[http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)

---

### Post by Diamond1984 on 2009-02-11
I've tried modifying the xorg conf file and still there is no change.  I get no new options under resolution even after reboot.  What is going on!
Here are the modifications I've made:
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
DefaultDepth 24

SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection

EndSection


Does my problem have anything to do with the fact that under "screen" it has "default screen" instead of configured screen? As a previous user commented it appears that my resolution settings are running in a kind of default/safe mode and I'm wondering if the default modes listed above are causing the problem. Can I simply change the "default" to "configured" or will this screw everything up? I appreciate all the help thus far and anyone else who can help.

---

### Post by Diamond1984 on 2009-02-11
-laptop:~$ dpkg -s xserver-xorg-video-trident
Package: xserver-xorg-video-trident
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 252
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:1.3.0-1build2
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-trident
Provides: xserver-xorg-video-4
Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2)
Conflicts: xserver-xorg-driver-trident
Description: X.Org X server -- Trident display driver
 This package provides the driver for Trident Blade/Image/ProVidia/TGUI/9xxx
 video cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This package is built from the X.org xf86-video-trident driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
evangeline@evangeline-laptop:~$

---

### Post by mikewhatever on 2009-02-11
Try modifying the Device section to the following:
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

---

### Post by Diamond1984 on 2009-02-12
I've made the modifications and there is still no change. Here is what my xorg conf file currently looks like.

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
DefaultDepth 24

SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection

EndSection

Thanks for you help so far I appreciate it.

---

### Post by jrrader on 2009-09-27
I realize this is really old, but I was having the same problem with my wife's Toshiba laptop and I just fixed it so anyone else who is looking for this.... 

There was no problem with my xorg but no matter what, when I started it up, it would go to a 1024x768.  For hers, she needs 1280x800.  xrandr said 1280x800 was the default, and I could choose it from the display configurations (only after changing it twice).  But on start up, it would always go back.

What I did create a new user on her computer.  I logged in with the new user and the screen resolution was 1280x800.  This means the problem was with my wife's account.  Back in her account I went into /home/(username)/.config/ and deleted the file monitors.xml

Problem solved.  Computer starts as it should.

---

