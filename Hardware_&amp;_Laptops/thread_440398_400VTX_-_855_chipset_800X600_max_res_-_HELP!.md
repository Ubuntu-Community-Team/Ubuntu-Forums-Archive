---
title: "400VTX - 855 chipset 800X600 max res - HELP!"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by LouisvilleLIP on 2007-05-11
I have a GTW 400vtx (855 chipset) that won't allow me to select a res higher than 800x600.  I've followed the [Hoary 855resolution ]("http://ubuntuforums.org/showthread.php?t=24923&page=3&highlight=855resolution") guide, and everything seemed to work, but I never got a higher resolution.

Can anyone confirm that the 400VTX is capable of displaying something higher than 800x600?

What do I need to do to troubleshoot this?  I've been over the steps in the guide multiple times, I'm not sure what else to do.  Thanks for any help...,

---

### Post by RTrev on 2007-05-11
> **LouisvilleLIP said:**
> I have a GTW 400vtx (855 chipset) that won't allow me to select a res higher than 800x600.  I've followed the [Hoary 855resolution ]("http://ubuntuforums.org/showthread.php?t=24923&page=3&highlight=855resolution") guide, and everything seemed to work, but I never got a higher resolution.

Can anyone confirm that the 400VTX is capable of displaying something higher than 800x600?

What do I need to do to troubleshoot this?  I've been over the steps in the guide multiple times, I'm not sure what else to do.  Thanks for any help...,

From a brief Google it appears to be able to do 1024x768.  What does your /etc/X11/xorg.conf look like?

---

### Post by LouisvilleLIP on 2007-05-11
Here is the relevant xorg.conf section. I added the Modeline in the "Monitor" section, it didn't previously exist.  


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  79
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by RTrev on 2007-05-11
Okay, I'm not sure about that modeline command.  What shows up in your xorg log file?  There should be some indication there if it's reading the request and rejecting it, or not even seeing it.

Go to the System menu, Administration, System Log, and then choose the Xorg one from your most recent boot.  Hopefully that will give someone here, if not necessarily me, an idea of what's going on.

---

### Post by LouisvilleLIP on 2007-05-11
Thanks for your help so far.

I'm not exactly sure what I'm looking for, and it's 1500+ lines, but this looks like it might be important.  I want 1024x768, I'm assuming that there should be a mode named that based on the statement below.  

If there is a different section that I need to list here, please let me know.

(II) VESA(0): Total Memory: 125 64KB banks (8000kB)
(II) VESA(0): Generic Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Generic Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using mode "1024x768" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)

---

### Post by RTrev on 2007-05-11
> **LouisvilleLIP said:**
> Thanks for your help so far.

I'm not exactly sure what I'm looking for, and it's 1500+ lines, but this looks like it might be important.  I want 1024x768, I'm assuming that there should be a mode named that based on the statement below.  

If there is a different section that I need to list here, please let me know.

(II) VESA(0): Total Memory: 125 64KB banks (8000kB)
(II) VESA(0): Generic Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Generic Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using mode "1024x768" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)

Well, I have two thoughts for you.  One is to make a backup of your xorg.conf file and then try something, and the other is to hold tight because I think I saw a thread recently where somebody is dealing with the 915 and is having to do weird things that I never heard of.  :)

If it were mine, I would make a backup of xorg.conf and then run this command:

```

sudo dpkg-reconfigure -phigh xserver.xorg

```

Make sure the driver you are using shows up, and select it, and then use the spacebar to put a mark next to each resolution you want to use.  This is the way I've been able to get increased resolution on every machine I've ever run Ubuntu on (come to think of it, that's a grand total of three! LOL!)

Hopefully this will work, and I'll go see if I can find that other thread in the meantime.

Bob

---

### Post by LouisvilleLIP on 2007-05-11
Well, 
sudo dpkg-reconfigure -phigh xserver.xorg
didn't work for me.  I get the following message:
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed


xserver does seem to be installed, and I tried to reinstall in Synaptic.  Any other ideas?

---

### Post by RTrev on 2007-05-11
> **LouisvilleLIP said:**
> Well, 
sudo dpkg-reconfigure -phigh xserver.xorg
didn't work for me.  I get the following message:
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed


xserver does seem to be installed, and I tried to reinstall in Synaptic.  Any other ideas?

Did you *move* your xorg.conf file, or did you just make a backup copy of it?  I've never known that command to fail.  But at least it gives us a lead.  For some reason your system doesn't think it's installed.  Why that would be is beyond my experience.

Anybody?  Why wouldn't this command work?  I have a hunch that when we answer that we'll have the solution to the problem also.

Sorry I couldn't help more!  :-(

---

### Post by LouisvilleLIP on 2007-05-11
I used CP to copy it to another location.  Synaptic thinks it is installed, and I can force it to reinstall, but it doesn't seem to have an impact.

---

### Post by RTrev on 2007-05-11
> **LouisvilleLIP said:**
> I used CP to copy it to another location.  Synaptic thinks it is installed, and I can force it to reinstall, but it doesn't seem to have an impact.

A quick Google suggests that some people lost their Xserver when they upgraded.  Did you upgrade or install clean?

Would you lose a lot if you were to try a clean install?  Try Googling "+xserver +855" and you'll see what I'm talking about.  One guy seemed to be in the same boat you are.. nothing fixed this short of doing a clean install.

I'm in an easy position in this regard.  My web work can just be FTP'd back down to my PC, and my applications are largely Firefox, Pan, Gedit, and GFtp.  So I just copy those folders from my home directory to a flash drive, reinstall, copy them back, set up the video again, tweak a few settings, and I'm off and running again.

If you're in a similar position, reinstalling might be the way to go.  It's what I would try, but I know nothing about your setup or what issues that might raise for you.

---

### Post by LouisvilleLIP on 2007-05-11
My clean install is only about a few days old, and I haven't done anything in Ubuntu yet, so everything should be working properly.  If I have to reinstall, I can, but I suspect that won't change anything.

Thanks again for your help so far. If there are any other suggestions, I'd love to hear them.

---

### Post by LouisvilleLIP on 2007-05-12
Anyone that can help?  I have a 855 chipset that maxes out at 800x600, I've tried the 855resolution patch but can't get anything higher than 8x6 in my screen resolution menus.

---

### Post by LouisvilleLIP on 2007-05-13
bump

---

### Post by LouisvilleLIP on 2007-05-17
I really want to ditch Windows for Ubuntu.  If I can't get a resolution better than 800x600, I can't justify the switch, it's too big of a pain in the butt.  Can anyone help me get anything higher than 800x600?

---

### Post by LouisvilleLIP on 2007-07-01
Does anyone out there know how to increase the resolution on a Gateway 400vtx laptop?  RIght now it maxes out at 800 x 600.

---

### Post by RTrev on 2007-07-01
Sorry to hear you're still having problems!  Is there a Restricted Drivers Manager option under your System | Administration menu?  I presume you've tried this, but if not it would be worth checking.  

Come on you guys, can't anyone help this poor guy?  :(

---

### Post by LouisvilleLIP on 2007-07-02
I do have the option, but it says no restricted drivers needed for my hardware.  Thanks again for trying to help.

---

