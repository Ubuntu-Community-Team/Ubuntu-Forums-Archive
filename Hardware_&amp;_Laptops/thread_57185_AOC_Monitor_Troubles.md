---
title: "AOC Monitor Troubles"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by jolstad on 2005-08-15
I have 10 AOC LM729 monitors running on Ubuntu machines.  Of those 10, 2 aren't working correctly.  I have sent them to AOC and they couldn't fine any problems and now one of them is worse.  

Basically the resolution will only display 640x480 @ 60Htz and all the rest do 1280x1024 with no problem.  I was able to get the resolution corrected on one by doing a dpkg-reconfigure xserver-xorg.  Now the colors are off on that one but I believe its the cable.

The other broken monitor I did the same thing to and I still have the small resolution.  I even hooked up a known working monitor to it and did dpkg-reconfigure xserver-xorg and it was good.  I then put the old monitor back on and as soon as I rebooted the resolution went back to 640x480.  Any help on this would be greatly appreciated.  My xorg.conf file is:

[SIZE=1]Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	128
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"AOC LM729"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"AOC LM729"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection[/SIZE]

---

### Post by moquist on 2005-08-16
Have you tried these monitors with Windows?  It would be interesting to know if the higher resolutions work ok then.  (Also, how about other Linux distros?)

Lastly, could you post the output from startx?  Just drop to the command line and run "sudo /etc/init.d/gdm stop", and then type CTRL-ALT-BACKSPACE on your X session if it's still running.  Then type ALT+F1 if necessary to change to a text terminal, and log in as yourself.  Run "startx > startx.log 2>&1" and X should start; use CTRL+ALT++ and CTRL+ALT+- to try to change your resolution.  Then kill X (either log out or CTRL+ALT+BACKSPACE again) and post the contents of startx.log here.

---

### Post by jolstad on 2005-08-16
Moquist

Here is the output:

xauth:  creating new authority file /admin/.Xauthority
xauth:  creating new authority file /admin/.Xauthority


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux video1 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:53:01 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 16 14:23:20 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0

---

### Post by jolstad on 2005-08-16
Moquist,

I was unable to get to a windows pc today to test the monitors.  I will try tomorrow hopefully.  Thanks for your help.

---

