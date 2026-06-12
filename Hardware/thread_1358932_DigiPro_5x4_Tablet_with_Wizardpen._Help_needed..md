---
title: "DigiPro 5x4 Tablet with Wizardpen. Help needed."
date: 2009-12-19
forum: Hardware
---

### Post by enixon on 2009-12-19
I've followed the tablet wizardpen setup instructions at [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) exactly and have run it to a little trouble.

I successfully calibrated the tablet then the tutorial asked me to save the calibration output and paste it into the x.org config file, Here are the exact instructions.

> Edit the file - Run this command:


sudo vim /etc/X11/xorg.conf
Press "I" - So that "-- INSERT --" appears!

Insert the output from calibrate into xorg.conf: (just place it below your generic mouse!)

Add the following line in the "ServerLayout" section:


InputDevice "WizardPen Tablet" "AlwaysCore"
Save the file, and exit the editor! (Press "ESC" and write ":wq" and press "Enter")[QUOTE][/QUOTE] 

Problem is I don't see any thing that say's Generic mouse to place it below nor do I see any thing that says ServerLayout so thinking it was me and not the file, I took a shot at it.

This is what my file now looks like,

> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
InputDevice "WizardPen Tablet" "AlwaysCore"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"

	Driver		"wizardpen"
	Option		"Device"	"/dev/tablet-event"
	Option		"TopX"		"3681"
	Option		"TopY"		"5250"
	Option		"BottomX"	"30708"
	Option		"BottomY"	"30496"
	Option		"MaxX"		"30708"
	Option		"MaxY"		"30496"

EndSection



And this is what it looked like before
> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"

EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"

EndSection



After I restarted my computer I got a warning telling me that ubuntu was starting in graphics low mode. This should be an easy fix, just set every thing back to normal, I'm just wondering how I'm supposed to leave the x.org config file in order to set up my tablet. Does my config file not look how it should by default or do I just not know what is what inside it. 

I can't be the only newbie who came across this, I would be very grateful if any of you could lend me your thoughts. btw I'm running 9.10.

Thanks

---

### Post by Favux on 2009-12-19
Hi enixon,

Karmic uses a wizardpen .fdi, not the xorg.conf which is why you're confused.  There's no "ServerLayout" anymore unless you add it, so you've added the "AlwaysCore" line to a video section.  Plus the "wizardpen" driver and the rest of the wizardpen stuff is in your video driver section rather than being in it's own section.

But none of that matters since you do not need to use xorg.conf.  So return it to the original state.  Then look at Dr. Kurian's [WizardPen HOW TO]("http://ubuntuforums.org/showthread.php?t=1337260").  That should get you set up.

---

### Post by enixon on 2009-12-19
Thank you for your help, I spent probably a total of 5 to 6 hours yesterday screwing around with it only to find out it was the outdated tutorial. Funny how reading the details can save you time. I went through the tutorial you posted and it now works like a charm. 

Thanks again, Big Help!

---

### Post by Favux on 2009-12-19
Hi enixon,

Outstanding!  You're welcome.

---

