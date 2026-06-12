---
title: "Ubuntu Screen Resoultion Problem With Toshiba Satellite A25-S207"
date: 2009-01-29
forum: Hardware
---

### Post by PoetGuy on 2009-01-29
I installed Ubuntu on this machine, everything works fine. Except for a major black border on my screen with the resolution. I googled several articles and changed the xorg.conf file different ways but i cant get it working, only the login screen fixes but as soon as i am logged in back it goes with the black border. Can anyone help please

---

### Post by dboe on 2009-03-20
Hello: I have the same screen resolution problem with my Toshiba Satellite A25-S207. Were you able to fix it?

---

### Post by ckalogr on 2009-04-15
Hello,
I am having the same problem with ubuntu 8.10.
It allows a max resolution of 800x600.
Have you found a solution?

---

### Post by ckalogr on 2009-04-15
Hello,
I think I fixed the problem.
use sudo gedit /etc/X11/xorg.conf to open the xorg.conf.
Then overwrite under "Section "Monitor" the following code:
Code:
Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

Save - Exit and then Log out and log in.
then configure display settings to 1024x768 resolution.
I hope it will  work.

---

### Post by crazypenguinguy on 2009-08-04
> **ckalogr said:**
> Hello,
I think I fixed the problem.
use sudo gedit /etc/X11/xorg.conf to open the xorg.conf.
Then overwrite under "Section "Monitor" the following code:
Code:
Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

Save - Exit and then Log out and log in.
then configure display settings to 1024x768 resolution.
I hope it will  work.
I just registered an account to say thank you. I had the same problem, and having just downloaded Ubuntu a few days ago for the first time, i kept running into the problems mentioned above, with no knowledge of how to fix it. You are my hero, as far as aspect ratios go.

---

### Post by sqeeeksLongboards on 2009-11-09
Just thought I'd let you guys know, 9.10 doesn't use an xorg.conf file unless you put one there, so if/when you upgrade, you'll either have to make your own or copy your old one to make it work. My advice is to keep a copy of your xorg.conf file if you reinstall, it saves a buttload of work on these things... took me two dang hours to get it to work the first time...

This is what my entire xorg.conf file looks like:

Section "Monitor"
	Identifier "Configured Monitor"
	Option "DPMS" "true"
	HorizSync 30.0-60.0
	VertRefresh 50.0-70.0
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
EndSection

Section "Device"
	Identifier "Trident Microsystems CyberBlade XPAi1"
	Driver "trident"
	BusID "PCI:1:0:0"
EndSection

The new Xorg apparently figures everything else out as it goes along, or something like that. Good luck.

---

### Post by Cpierce on 2010-09-21
This is the exact problem I have as well. However, I am using Lubuntu which uses xsesson instead of xorg ? How would I fix this ? 

My card is a Trident microsystems Cyberblade/XP

---

### Post by mrnettles on 2010-12-19
I have exactly the same problem with 10.10 Maverick on a Toshiba laptop. The text file in the above posts is blank on my machine. I'm a total beginner and have no idea what to do. Please help!

---

### Post by Stephann on 2011-02-08
Briefly, I also wanted to say thank you.  I'm on a Mac G4 PowerPC running Lucid, and xrandr didn't correctly identify my monitor's capabilities, and I didn't have an xorg.conf file generated (it just wasn't there.)  By adding my monitors max resolution to the list (in my case, it was 1440x900) and saving the file in /etc/X11/xorg.conf, it worked like a charm.

Many thanks!

---

### Post by Garrett77 on 2011-04-16
I am having the same problem and I am a total newb.  I tried to create the file in the appropriate directory then restart.  The computer started then sat at a prompt instead of getting into the GUI.  Through other threads I learned how to delete files (rm) and i removed the xorg.conf file and restarted.  Started up like normal.  Not sure what I am doing wrong.  I am running Ubuntu 10.10 Maverick.  Any help would be APPRECIATED!!!!!

---

