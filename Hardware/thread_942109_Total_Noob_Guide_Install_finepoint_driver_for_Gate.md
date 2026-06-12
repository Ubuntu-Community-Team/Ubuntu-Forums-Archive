---
title: "Total Noob Guide: Install finepoint driver for Gateway CX2724"
date: 2008-10-08
forum: Hardware
---

### Post by sjoz on 2008-10-08
Hello all!

First off, none of this information is mine, it's all gathered from other forums and it's the exact steps, in order, that I took to get ubuntu usable in tablet mode on my Gateway CX2724.

There was a LOT of information posted when I was trying to figure out how to install this, and I really wished someone would post a simple step-by-step guide to help a complete idiot install this. 

Anyways, in the spirit of Ubuntu, I'll attempt to give back to the community by posting a guide, and I hope it will help others in my position.
Everything is done from a fresh install of ubuntu.

How to install finepoint Stylus on Gateway CX 2724:
===================================================

1) Install setserial via System/Administration/Synaptics Package Manager

2) Enable SetSerial through  System/Administration/Services

3) Download the driver posted on this page: [http://ubuntuforums.org/showthread.php?t=763380](http://ubuntuforums.org/showthread.php?t=763380) by ace214. This should be a direct link to the driver, so that you don't get confused: [http://ubuntuforums.org/attachment.php?attachmentid=68137&d=1209568540](http://ubuntuforums.org/attachment.php?attachmentid=68137&d=1209568540)

4) Extract the driver to your desktop, or another location

5) Using Terminal, browse to Desktop, or wherever you saved the driver.

6) Move the driver using the following code in terminal

	sudo mv fpit_drv.so /usr/lib/xorg/modules/input/


7) Add the following lines of code to the file /etc/serial.conf, using sudo gedit /etc/serial.conf or sudo nano /etc/serial.conf

	/dev/ttyS0 autoconfig
	/dev/ttyS0 uart 16550A port 0x3f8 irq 4 baud_base 34800

8) Add the following to your /etc/X11/xorg.conf file, using sudo gedit /etc/X11/xorg.conf or sudo nano /etc/X11/xorg.conf

	i) Put this after an InputDevice section

  Section "InputDevice"
  Identifier  "Tablet"
  Driver      "fpit"
  Option      "Device"           "/dev/ttyS0"
  Option      "InvertY"
  Option      "MaximumXPosition" "12550"
  Option      "MaximumYPosition" "7650"
  Option      "MinimumXPosition" "400"
  Option      "MinimumYPosition" "400"
  Option      "SendCoreEvents" "true"
  Option      "Passive" "false"
  Option      "TrackRandR" "on"
  EndSection


	ii) Put this in the "ServerLayout" section, after InputDevice "Synaptics Touchpad", or whatever. So long as it's in the section.

  InputDevice	"Tablet"

9) Reboot


I have done this twice now, and the calibration and left click work very well. The right click does not work, but for basic needs (note-taking without Windows) it will do. 

Have not yet worked with screen rotation. 


Hope this guide helps!

		
Please feel free to correct any of this, but it's EXACTLY what I did, and my stylus works quite well, to a limited capacity (no right click).

---

### Post by bilal.17 on 2008-10-09
I have the Gateway CX2724, and thanks for putting this up as I have been looking for a walkthrough on how to set up my pen. I have been looking on my own, but haven't had the time to finish. Anyhow I followed your instructions perfectly. When I rebooted it came up in low graphics mode and the pen did not work at all. So what I did was reversed the steps I did and now it boots fine. 

I think the problem may be linked that i did not have a serial.conf file and had to create one. I will try again at a later date.

---

### Post by jay12701 on 2008-10-27
Thanks for the how to. I've been trying to get the finepoint drivers working for about 2 years now with no luck. Followed this and had it working in about 5 minutes. Think I was just having problems getting the setserial running before. 

Thanks again.

---

### Post by sjoz on 2008-10-30
Sorry to the guy who didn't get it working, but I'm glad that someone else was able to benefit from the howto.

---

### Post by Vexamus on 2008-11-11
Unfortunately, this doesn't work in 8.10 at all, the xorg.conf is hardly used and if you add the rest of the ServerLayout section it won't load the window manager at all.

Has anyone else gotten this to work in 8.10?

---

### Post by jay12701 on 2008-11-11
I actually have only gotten it to work so far in 8.10. A friend of mine has also gotten it to work on a M series gateway in 8.10, but only when commenting out a line in the fine point source, then recompiling it.

---

### Post by Vexamus on 2008-11-12
So what did you have to do differently, my xorg.conf has barely anything in it??

---

### Post by bilal.17 on 2008-11-15
I have finally been able to get it work. For some reason I did not have the serial.conf file in the /etc/ directory. Eventually I found it in /usr/share/doc/seterial/ and after that I followed the steps and voila now my pen works. Thank you sjoz for the guide that you provided.

---

### Post by jay12701 on 2008-11-17
I think it will work if you upgrade from Hardy. When you do that your xorg.conf is preserved and you will be able to make it work. I know I had upgraded from Hardy to the Ibex beta about a week before I got this working. My friend who got it working ended up just scrapping his original install then putting hardy on it. I can't remember if he installed the finepoint drivers and then upgraded or upgraded first, but either way this keeps the xorg preserved. 

You could try adding the sections to the xorg, not sure if that works or not, but worth a try.

---

### Post by taylorsellers on 2008-12-01
Sorry to bump an aging thread, but I found it extremely helpful and it pointed me in the right direction to solve my own issues introduced with a fresh install of 8.10 (rather than an upgrade from Hardy). A previous poster had said something about his friend scrapping his 8.10 install and just going with hardy to make it work, but I didn't want to do that since I had already spent a significant amount of time customising and tweaking my Ibex install. In the spirit of the "Total Noob Guide" I thought I would offer my experiences as a supplement to sjoz's guide for those that are trying to follow the steps with a fresh install of Ibex, having never upgraded from a previous version. I will also add that my tablet is a Gateway CX2619 rather than a CX2724, however I believe they use the same digitizer.

Installing finepoint Stylus on Gateway CX2619 with non-upgrade Ibex:
====================================================================

1) See sjoz's guide above.

2) See sjoz's guide above.

3) See sjoz's guide above.

4) See sjoz's guide above.

5) See sjoz's guide above.

6) See sjoz's guide above.

7) The latest version of setserial (which **will** be the one you get through Synaptic if you install it after Ibex was released) does not automatically put the serial.conf file in your /etc/ directory. However, setserial still looks in the /etc/ directory for the conf file rather than its new location. I am not sure if any of this behavior is unintended, but it needs to be moved in order to work for our purposes. The serial.conf file, as confirmed by bilal.17, is located in the /usr/share/doc/setserial/ directory. Open a terminal and navigate to this directory. Then, move it to the /etc/ directory with the following command:

```
sudo mv serial.conf /etc/
```

At this point, follow sjoz's 7th step above.

8 )This step also presents an issue for users with standalone Ibex installations. As noted several times previously in this thread, Ibex's xorg.conf file is extremely small and notably does not contain a "ServerLayout" section. Simply adding a server layout section made my system unbootable. Knowing that these steps work with a hardy install, I set out to find a xorg.conf for hardy that I could substitute for my Ibex one. Ultimately, I ended up downloading an ISO for a hardy LiveCD, booted it up and looked at the xorg.conf there. Since my Ibex installation was still on my hard disk, it was just a matter of copying and pasting the hardy xorg.conf to my ibex xorg.conf. I then added the lines in step 8 of sjoz's guide. My final xorg.conf (the one I use in Ibex) looks like this:

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
	Option		"RightEdge"		"5820"
EndSection

Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "InvertY"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
	Option "SendCoreEvents" "true"
	Option "Passive" "false"
	Option "TrackRandR" "on"
EndSection

Section "Device"
	Identifier "Configured Video Device"
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
	InputDevice	"Tablet"
EndSection
```

This xorg.conf, with all of the other steps, gives me perfect pen tracking and left click functionality. The xorg.conf file contains no other modifications other than a single line in the touchpad section ("RightEdge") designed to reduce the size of the vertical scroll portion of the touchpad, which was actually twice as wide as it should have been.

If this xorg.conf works for others, that is great. If not, I would recommend booting a LiveCD of hardy and getting your own xorg.conf tailored to your hardware.

9) Reboot

---

### Post by jay12701 on 2008-12-01
Yeah the mouse thing has been bugging me forever...thanks for a possible fix on that, I'll be trying it out later tonight. 

Also, I think the serial.conf hasn't been there for a couple distros. When I was fiddling with this back in gusty it wasn't there.

---

### Post by 1hunter8 on 2008-12-02
I agree with you!![img]http://links.longhainet.com/haha.jpg[/img]-----------------------------------------------------------------------------------------------------------------------------------Signed Network: Not A Bad Man, A Woman Does Not Love!Recommendation:[Injection Mold](http://www.hitop-mould.com/injection-mold.asp) / [Plastic Mold](http://www.hitop-mould.com/plastic-mold.asp) / [Mold Maker](http://www.hitop-mould.com/mold-maker.asp) / [Mold Making](http://www.hitop-mould.com/mold-making.asp) / [Mold Manufacturer](http://www.hitop-mould.com/mold-manufacturer.asp)

---

### Post by heatheriac on 2008-12-29
Okay, i got this whole thing running using the modified walk through, but i'm having insane sensitivity on the pen.  if i keep the pen a 1/4 inch from the screen, it keeps sending left click commands to the system.  a test on this page has it reloading every two seconds, and the desktop started making tons of new folders.  Is there a way to disable the right click function for just the pen?

---

### Post by Favux on 2008-12-29
Hi everyone,

The problem with xorg.conf you've experienced was intentional.  In Intrepid Ubuntu started moving to HAL (hardware abstraction layer).  This offers hotplugging and other technical advances.  This was suppose to allow tablet support "out of the box".  Unfortunately it turns out there's a limitation on HAL, so that it does not support tablet pc's much beyond stylus.  So us tablet users have to "revert" to xorg.conf.  Recognizing this supposedly Ubuntu has promised Jaunty will have more support for tablet pc's in xorg.conf, etc.

Loic2 is one of the users involved in this.  See his Wacom wiki for more details:
[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

With regard to right click button activity, at least one Wacom serial tablet user said this worked for him:
```
	Option		"Button2"	"3"  # make side-switch a right button
```
which is in my xorg.conf's stylus section like so:
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"USB"		"on"
	Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
	Option		"Type"		"stylus"
	Option		"Button2"	"3"  # make side-switch a right button
	Option		"TopX"		"225"
	Option		"TopY"		"225"
	Option		"BottomX"	"26300"
	Option		"BottomY"	"16375"
EndSection
```
Does the Fujitsu finepoint (fpit) driver include option parameters like this Wacom one?  I think 1,2,3 are the button numbers, so I suppose you could try various combinations.

---

### Post by Havok0388 on 2009-02-02
Hey guys. Been stalking these forums for a while now, and they've been a huge help since I started playing with linux about 6 months ago. I have to say this has been one of the most helpful things I have found, having a Gateway cx2619 myself. I am thrilled to have my tablet functionality back, as it was the only thing I missed from the default windows install!

Thanks for great guide!

---

### Post by stevex on 2009-02-07
I can use the stylus now find as a mouse.  What do I need (or is it even possible) to use the stylus to write with xubuntu 8.10 and a Gateway CX2620

---

### Post by Favux on 2009-02-07
Hi stevex,

Have you tried Xournal or CellWriter?  Check in Synaptics.

---

### Post by Zuke24 on 2009-07-24
This guide is great!  It's really giving me a good starting point.  However, I'm using Koala . . . and these steps don't seem to be working for me.  It's not keeping me from booting up, either, so that's a good sign.

My tablet is a CX2726, which I believe has the exact same digitizer as the other ones listed here.  Any ideas on where to look to troubleshoot this?  Thanks!

---

