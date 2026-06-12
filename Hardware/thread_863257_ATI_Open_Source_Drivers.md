---
title: "ATI Open Source Drivers"
date: 2008-07-18
forum: Hardware
---

### Post by BoarderX2k3 on 2008-07-18
I attempted to install a Radeon 9250 PCI video card on an older Dell Dimension 2400 yesterday. Despite the fact that the open source ATI drivers are supposed to be shipped with Hardy, I can't seem to get them working. I can't use the proprietary ATI drivers because they don't work with my Radeon model. I have to boot into low-graphics mode every time. 

I have been following directions [here]("https://help.ubuntu.com/community/RadeonDriver"). I've tried everything possible I can think of. 

My question is this: If I try to do a fresh install of Hardy, is there any chance that may solve the problem?

---

### Post by ajgreeny on 2008-07-18
In your low graphics mode use Alt+F2 to get a "Run" dialog box and enter ```
gksudo displayconfig-gtk
``` This will open up the Screens and Graphics window where you should be able to change the graphics driver.  Go to Graphics Card tab, "Chose driver by model", select **ATI** and then **Radeon (fglrx)**.  This is still the open source driver, in spite of the fglrx in brackets.  This is how mine is set at least, and although I have the 9200SE card, I think it should be the same for yours.

---

### Post by BoarderX2k3 on 2008-07-18
ajgreeny, thank you so much for replying!

Unfortunately, I had already tried that to no avail. Whenever I change any of those settings, they just revert back after I restart the computer. Attached is a screenshot of what it reverts to.

Here is a portion my current xorg.conf file:
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS73"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SDM-HS73"
	DefaultDepth	16
```

This is incorrect. My xorg file has not been updated for the new video card. When I execute this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure my xorg.conf file, I get this:

```
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
EndSection
```

Which is still incorrect. I know that the video card is there and can be detected because

```
lspci -nn | grep VGA
```

returns:
```

01:04.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
```

I'm not sure where to go from here. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) says that the driver and server should autodetect most settings but that isn't happening for me. 

please help! :confused:

---

### Post by ajgreeny on 2008-07-19
You appear to have two graphics cards in your machine.  Is that true, do you have an onboard and a pci card installed, or is that just a result of what you have been doing?  I think the vesa driver listed is simply the low res driver that is causing the problem.

Try running in console mode (Ctrl+Alt+F1) stopping the x session with ```
sudo /etc/init.d/gdm stop
```then running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```and chosing the right driver when you get to that point.  Now use ```
sudo /etc/init.d/gdm start
```and with luck all will be OK.

If that is no good, it could be worth using recovery mode from the grub menu (second down, probably) and using the xfix option there.  I have never used this but have read about it here in the forum, so can't help further on the details of that, I'm afraid.

---

### Post by Chazzer on 2008-09-24
I have been using Ubuntu Hardy for several months, and although this is mostly with great pleasure I must say I've been frustrated with the support for my ATI Radeon 9250. 

Using the instructions given on this thread, I have tried to improve my graphics capability but without complete success. The problem described by BoarderX2k3 very closely resembles my own although I have managed to get out of low-graphics, I am running 1280x1024 at the moment but I am not entirely satisfied. This ATI card is supposed to have 256mb of video memory but I'm somewhat underwhelmed by my lack of color control. Also I can't choose to have any visual effects whatsoever. If I do my system will slow down to a snails pace every time I try to move a window.  I can live without the eye candy but I would certainly like to be able to manually set gamma controls for colour, which is important to me as I'm a designer.

When I choose Monitor Settings it says I am running pci:01:00.0-1:VESA standard monitor.  When I run gksudo displayconfig-gtk it envokes the screen and graphics preferences which tell me I'm running ATI Radeon (fglrx) and an IIyama Prolite display which is correct. 

Somehow I managed to install an ATI Catalyst Control Center which is listed in my Applications menu. It doesn't work however as I it says "no ATI driver is installed". I have tried to install the ATI driver (I guess that's how the Catalyst Control Center is in the Apps menu) but without success.  If I try and choose the proprietary driver from within the screen and graphics preferences (as it is listed there) I am cast into low-graphics mode once again.

I have read on this forum that there's a bug in the ATI fglrx DVI output and the user needs to re-compile the driver.  I'm sure I've tried it all.

Should I be happy?  Is this the best I'm likely to get with this equipment?  Should I get a better computer and avoid ATI graphic cards?

---

### Post by markbuntu on 2008-09-24
The ati proprietary driver does not support your card so forget about that. What you need is the latest Radeon driver which has full support for your card.

---

