---
title: "fglrx and xorg.conf"
date: 2013-09-18
forum: Hardware
---

### Post by hurrrtin on 2013-09-18
I've been trying various things for a week now, and I can not seem to get it just right. 

My setup is like this: I have two monitors of the same make and model on the same one card. I need the monitor on the right to be the primary, and the monitor on the left to be left of the right. Additionally, I tried using the ubuntu display utility to move the monitors that way, but that's made things worse. So I'd like to do two things:

1.) Delete any settings that may be messing with the display config so that it's all just as the xorg.conf defines it (hopefully without reinstalling.) I've already tried wiping the user's home folder, but it still flickers around a bunch when logging in.

2.) Fix up my xorg.conf so that it is correctly configured: Monitor on the right should be the primary display for logging in once logged in, with the UI on the right screen, and be able to move the mouse to the left to reach the left monitor.

Here's my current xorg.conf:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "dri"
	Load  "glamoregl"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP9"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP10"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Monitor-DFP9" "0-DFP9"
	Option	    "Monitor-DFP10" "0-DFP10"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 1920
		Depth     24
	EndSubSection
EndSection

```


I'd also settle for being able to have each screen be it's own desktop so long as I can move the mouse in between them. It's not as important if I can drag windows between them or not.

I appreciate your help. Thanks!

---

### Post by QIII on 2013-09-18
Hello!

With the exception of setting the primary monitor, you should make all changes either with CCC if you are using the fglrx driver or the display setup utility if you are using the open source driver.  Don't try to mix and match.

Primary display should be set using the display setup utility in either case.

Unless you have some sort of special setup, you shouldn't need to make any adjustments to your xorg.conf by hand.

If you look at the ATI Driver wiki link in my signature, go to section "2.1. Installing via the command line".  If you are using 13.04, you can ignore the warning about the -updates version of the driver.  That seems to work now (and I need to update the wiki.)

After it is installed, use the Catalyst Control Center to span your desktop across both monitors.  In my case, I have three monitors, but take a look at the Multi-Display tab.  You want "Multi-display desktop with display(s) x,y" so that the fish spans across both screens:

[ATTACH=CONFIG]246318[/ATTACH]

Then use the display manager only to set the primary screen.

Let us know if this helps.

Best wishes!

---

### Post by hurrrtin on 2013-09-18
I've used that tool extensively. It doesn't help anything. All kinds of new little entries pop up in the config file, but it behaves the same. Best I can get is having to move the mouse to the right of the primary to reach the left monitor.

I've read many posts and tricks, such as using gksu as opposed to gksudo, etc. It seems I have no choice but to do so manually for whatever reason. I can only guess that something is overriding the xorg.conf somewhere in the process because of a lack of something there...

---

### Post by QIII on 2013-09-18
Did you set it up with Catalyst and then use Ubuntu's display manager only to set the primary?

---

### Post by hurrrtin on 2013-09-18
Yes I did. To no avail. Which has led me to various attempts with aticonfig, etc.

Do you know off hand, if I use ubuntu's display manager, are those settings system wide, or does that affect the current user only? Because I have made changes that didn't work, blown away the user directory and made other users, and yet the screen still flickers around and does odd stuff even after doing so.

---

