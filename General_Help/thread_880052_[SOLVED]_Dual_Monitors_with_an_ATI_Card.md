---
title: "[SOLVED] Dual Monitors with an ATI Card?"
date: 2008-08-04
forum: General Help
---

### Post by Tindytim on 2008-08-04
Recently installed Ubuntu (again), and installed the proprietary drivers for my Card (X850).

I've done some reading, and searching, but most of the information I've found is about methods that are running multiple desktop instances, or have been for Nvidia card (And also appear to be for older versions of Ubuntu). I'm also unfamiliar with Ubuntu command line syntax.

How would I go about getting both Monitors working, possibly with the ability to drag windows between them?

Is this the proper place for this?

---

### Post by gnat79 on 2008-08-04
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

I set up dual monitors at work (don't have the xorg file handy, sorry). It was as easy as adding a couple of lines to /etc/X11/xorg.conf . I think the link above describes what I did in the "twinview" section.

As far as command line syntax, pretty much all GNU/Linux systems use the BASH shell and GNU tools. The only differences are some system specific things like the package manager.

Most of these tutorials show you exactly what to type into the shell, so it's not too hard. Lots of them even explain what each thing does.

Oops! I just noticed that twinview is only for nVideous cards, so you'll have to try one of the other approaches.

---

### Post by mrmiserable on 2008-08-04
firstly how exactly did you install driver
have you got ati control panel this sets up dual screen easy

i have used dual screen with ati card a long time ago but compiz and my crap X600 card resolution was poor so try 

in terminal 
aticonfig --query-monitor 

this will give your monitors then add that to your xorg.conf like below but with (your monitors)
then the pairmode option i had to lower to set a maximum of 2048 for compiz but if your card gives higher modes great test by typing compiz it will tell you maximum  

here is part of my old Xorg.conf

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "AllowGLXWithComposite" "true"
	Option	    "AccelMethod" "XAA"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1024x1024+1024x1024,0x0+0x0"
	Option	    "EnableMonitor" "tmds1,crt1"
	BusID       "PCI:1:0:0"
EndSection

maybe play with the options to suit your card and resolution modes

if you need more help 
i will check back tommorrow

---

### Post by Tindytim on 2008-08-05
Well I recently installed the drivers from the ATI site (previously having installed it using the Synaptic Package Manager). I had some issue running the Catalyst controller center (which I didn't appear to have until I installed the driver from the ATI/AMD site), which I researched, and apparently is has something to do with me running x64 Ubuntu (probably should have mentioned that earlier).

I've tinkered with the xorg.conf file, and now both monitors are stuck at 800x600, and when I type "aticonfig --query-monitor" it outputs
```
  Connected monitors: none
  Enabled monitors: none
```
Before I messed with the xorg file "aticonfig --query-monitor" gave me an error.

I've taken out all of the line I added to the file, and I'm still stuck without any other display options. I'll look for some information on the xorg file, and try to get the drivers working normally.

---

### Post by mrmiserable on 2008-08-05
ok if you put new setting in screen section of xorg then upon reboot goto preferences/screen rosolution and choose new setting as default mine was set at 2048x1024 because of last post but you can choose your maximum for yours give it a try it worked for me

good luck im here now if you need more info

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "2048x1024" "1280x1024" "1024x768"
EndSubSection
EndSection

also for installation check you have all needed packages this guide is good

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Tindytim on 2008-08-06
Well, I'm now just going to get a new Nvidia card to tide me over for a while (9800 GTX), so I'll just have to delay my work for a few days.

---

