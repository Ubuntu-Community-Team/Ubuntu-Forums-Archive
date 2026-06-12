---
title: "Problem with Intel Integrated Card and Wide-screen"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by mat42187 on 2006-12-10
As a forward, I'm a newbie to Ubuntu, but have had limited experience with other distros. Anyways,

I recently installed Ubuntu 6.10 onto my HP Pavilion with the ViewSonic VA2012wb monitor, which is a 20.1" wide-screen monitor. I have been looking around the forums, trying to understand how to change my xorg.conf file but when I go to the file, it seems that everything is there. My resolution is in there and it even knows what monitor I'm using. But the max rez I can set it at is 1600x1200, rather than 1680x1050 it should be.

Maybe someone can help me out. Thanks for all of the help, here's the portion of the config file...


```

Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"VA2012wSERIE"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"VA2012wSERIE"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

### Post by drphilngood on 2006-12-10
Try using this guide:

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

and if you have trouble or still need help post back.

---

### Post by mat42187 on 2006-12-10
I tried making my own modeline, but it didn't work. Maybe I'm putting it in the wrong place or forgetting something. I added

```
 # V-freq: 75.00 Hz  // h-freq: 82.46 KHz
 Modeline "1680x1050" 207.14  1680 1784 2032 2512  1050 1050 1053 1099 
```

to the "Monitor" section and that didn't work. I also changed the refresh rates along with it and that did not work.

I just think that it's weird because looking at my xorg config, it looks like it recognizes everything (the desired rez is listed in the "Screen section")

---

### Post by evilghost on 2006-12-10
Search these forums on the term '915resolution' as this will likely be your fix.  I had to do it on the wife's machine to get 1440x900 and seems to be SOP for any intel embedded graphics card.

---

### Post by dmartinsca on 2006-12-10
> A short explanation of 915resolution & why it's needed as far as i understand it: The X Windows system for linux only displays resolutions which are programmed into the BIOS of the video card. The Intel video cards only include standard VESA resolutions in their BIOS -- this doesn't include 1440x900 or 1280x800 or any other common widescreen LCD resolutions. 915resolution writes over one of the pre-programmed resolutions of your video card's BIOS (which you won't use anyways;) )so that Xorg can use it. Now, this change only occurs in memory which is lost when the computer is turned off/rebooted. That means 915resolution needs to run every time linux boots. **_It also means that no harm can be done to your video card, so don't worry 'bout that :)_**
Just installing 915resolution & the vbetool packages through synaptic or aptitude, then logging out and restarting the display by pressing Ctrl+Alt+Backspace should be enough to get you the proper resolution (assuming it is the first resolution in the list in your xorg.conf). If this doesn't work, try rebooting the computer. Installing 915resolution automatically sets it to run at boot, and the vbetool package allows it to configure it's self for your video card/monitor.

---

### Post by mat42187 on 2006-12-12
Thanks for the help guys!

I messed around with 915resolution and the xorg.conf file and somehow broke my Ubuntu (as in not even having a command line interface to restore the xorg file, heh...oh well) 
So I'm going to fresh install when I find some time and try again, going a different route. I'll post back with an update.

Thanks again!

---

### Post by mat42187 on 2006-12-17
ok, i finally got 915resolution to work and after restarting the display, it's working. thanks!

---

### Post by Tasu on 2006-12-22
Well! Ok! Please can you post the solution and the steps you made to success on it, so other people in your situation would benefit from your experience?

Thanx

---

### Post by mat42187 on 2006-12-24
No problem.

After installing 915resolution,

    * Run the following to see the availible modes: (might need sudo)

```
915resolution -l
```

    * Choose a resolution you don't need and replace, for example the following changes 1920x1440 to 1920x1200 

```
915resolution 5c 1920 1200
```

    *Then exit the command line and reset your computer, and then reset the display by pressing Ctl+Alt+Backspace

    * This should add the option for that resolution to the "System>Preferences>Screen Resolution" tool.
    * If it works correctly then you can make the change permanent: 

```
sudo gedit /etc/rc.local
```

    * Simply add the command you typed in above before: 

```
exit 0
```

Most of this is from UbuntuGuide.org

---

