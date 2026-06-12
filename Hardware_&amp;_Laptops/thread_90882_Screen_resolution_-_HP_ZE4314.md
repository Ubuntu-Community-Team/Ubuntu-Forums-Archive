---
title: "Screen resolution - HP ZE4314"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by pclyne on 2005-11-16
I'm a Noobie so appoligies if this _has_ already ben answered or I have posted to the wrong forum.

I have a ZE4314 laptop running Kubuntu 5.10 and Whilst there are a few things i can't sort out I must say that in general "IT ROCKS !!":D 

One of the things on my list is trying to increase the resolution from 1024*726 to the same as my 'other' laptop - which runs a competing main$tream product.

I really would like to get to 1400*1050.

I've read forums, searched for the ATI driver thats appropiate (it's reported in xorg.conf as a "Radeon 330M/340M/350M (RS200 IGP)"), Edited xorg.conf, re-read forums and sworn at it (I'll cry if it'll help)

The more i read the more confused I get.:confused: One post somewhere suggests I download and recompile a new driver.  I would be happy with that _except_ I'm not sure it's for KDE nor 5.10 - and not being able to find the appropiate driver (well it's not immediately obvious to me) adds a certain degree of difficulty 

Can somebody PLEASE take me on a step by simple step journey as to what I need to do..

Big thanks in anticipation....

---

### Post by Daniele Di Pietro on 2005-11-16
I would first suggest to try with "ati" driver (the free one, supplied with your distribution). Check that your /etc/X11/xorg.conf file contains something like

*** BEGIN LISTING ***

Section "Device"
	Identifier	"<Your graphic card name>"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"<Your graphic card name>"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

*** END LISTING ***

Please note that the mode you want to display must be present in the "Screen" section.

I hope it helps. Bests,
Daniele

---

### Post by chook on 2005-11-16
Can you remember if you were offered a series of resolutions during the second part of your installation?If so, then why not just reinstall,then select the resolutions you want.If you do this make sure you press the space bar when the curser is next to the resolution you choose,this adds a * under the curser telling you it has been selected.I would suggest about 5 different resolutions.When your screen loads it should default to the maximum. It sounds a pain but I think compiling new drivers could be a little out of us newbies league.
good luck,
Chook.

---

### Post by Daniele Di Pietro on 2005-11-16
Easier than reinstalling you can reconfigure the X server using
sudo Xorg-configure

---

### Post by ispiked on 2005-11-16
Something to keep in mind: unlike CRTs, LCDs only support one native resolution. So if you try to run at anything larger or smaller than that, it usually ends up looking pretty bad.

---

### Post by Shaggy on 2005-11-16
If you're using the packages that came with Ubuntu, that's why you're not getting anything above 1024.

Download the deb package off of ati's website and install it.
```
sudo dpkg -i *packagename*
```

---

### Post by pclyne on 2005-11-16
Firstly, **BIG THANKS** to all who replied


I think I have a result on this (not one I'm 100% happy with - but result all the same).

It would appear (after spending a _very_ long time on the phone to HP) that there were two model 4314's released.  One supports 1400*1050 the other only supports 1024*768.

Guess which model I have :( 

So it seems i'm stuck with the resolution I have.

(unless shaggy's suggestion can force the screen to behave 'better':confused: .  The question is what driver:confused: Whilst i can find the Linux section of the ATI web site - there are too many choices for me to understand {best _guess_  X.Org 6.8 8.19.00 file?}.

So if you have nothing better to do 'solve' then feel free to offer more assistance, but don't feel compelled {i'll just live with my 'lower' resolution}

---

