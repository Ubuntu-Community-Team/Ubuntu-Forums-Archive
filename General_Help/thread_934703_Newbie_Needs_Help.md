---
title: "Newbie Needs Help"
date: 2008-09-30
forum: General Help
---

### Post by homicidalpossum on 2008-09-30
Hi sorry I am new, but everyone must start somewhere :)
I am very impressed with this operating system so far but I have run into my first problem. I have done a forum search but the replies were either too confusing or irrelevant or I was too nervous to try it in fear that it would be the wrong driver and I would cause myself more problems.

Basically I have fresh installed Ubuntu Desktop Edition but I have not got any drivers yet, in windows I would just install the EXE and run it and that was all. But I am confused when it comes to installing my drivers here, I hope one of you could take the time to help teach me I would be extremely grateful and it would help me out a bunch. I have been using computers for a long time and even took a IT course at college but it was all window based, so I am not completely computer illiterate just Linux is something I have never used so I am currently pretty confused. 

My video driver is my main driver I would like to get. As far as I know it is a MOBILITY RADEON 9000 IGP.

Here is a link to the exact spec of all of my computer :) [http://reviews.cnet.com/laptops/toshiba-satellite-a75-s211/4507-3121_7-31264915.html]("http://reviews.cnet.com/laptops/toshiba-satellite-a75-s211/4507-3121_7-31264915.html")

I can hear sound on my laptop, but do I need to install a sound driver (would it improve the sound quality) sorry if my questions are kind of silly I am still learning :(

I have internet so I am guessing I don't need to install any network drivers?

I basically want to get my system to the point where I can play games on it, I found some guides to getting world of warcraft to work on Linux as this is the game I play, so I would like to get my computer to the stage where I can play this game.

Based on the spec, etc. of my laptop what other drivers do you think Iwould need?
Any help would be very much appreciated, thank you in advance :).

Chris

---

### Post by doas777 on 2008-09-30
I hadn't really noticed until you asked, but i don't really install drivers on ubuntu. there are two notable exceptions however: Videocard and wireless nic. the headaches associated with these however more than make up for the absence of updating chipset drivers.

for your video card, go to System -> Administration -> Hardware Drivers .
hopefully you will notice a restricted driver listed. just enable it, and you should be ready to go. 

I'm an nvidia guy, so I can't help, but there are innumerable threads and tutorials on installing ATI drivers.

good luck,
Franklin

---

### Post by tuxxy on 2008-09-30
Video driver - system > admin > hardware drivers enable the driver here if there isnt one listed try using envyng application to install the driver.

envyng is available in the repos, search for envyng-gtk using synaptic or type in terminal

```
sudo apt-get install envyng-gtk
```

Sound usually works fine with ALSA as the output, navigate to system > prefs > sound and select ALSA as tthe output device, now play the test sound file to check.

---

### Post by mikewhatever on 2008-09-30
Most of the drivers are included on the CD and loaded during the installation, as Ubuntu installer detects your hardware. Ubuntu is quite good at it, nevertheless, check under System->Admin->Hardware drivers, some firmware can't be pre-loaded because of licensing and philosophical issues. Your sound works, so I don't recommend tweaking, unless the sound quality is really bad.
Generally speaking, Linux is different. Many thing are not the same as in Windows, as you'll discover soon enough.

---

### Post by homicidalpossum on 2008-09-30
Hi guys, thanks for the replies. In the Hardware drivers section the only drivers listed are the ones for my network card none for my graphics card.

Tuxxy you speak of the envyng application but I am wondering what exactly it  before I install it, does it just suggest some available drivers like the hardware drivers section does? Or do use it to open a driver file? Sorry I am so new at this :P
I have installed to my knowledge the envyng program through synaptic, but I dont know how to get to it or what to do next lol :S

---

### Post by mikewhatever on 2008-09-30
It's odd, I expected the graphics driver would be there. Can you open Applications->Accessories->Terminal and post the output of the following:
> cat /etc/X11/xorg.conf.
Just wondering what driver is in use.

---

### Post by homicidalpossum on 2008-09-30
Managed to get envyng working but I get an error when trying to install the driver.

Its basicaly says

Ubuntu Hardy 32bit
Your graphics card has been detected as ATI Mobility Radeon 9000/9100 IGP Series 
Your graphics card is supported by the legacy driver
EnvyNG error ATI's legacy drivers do not support your operating system


So it seems that the idea of envyng doesn't work :(
Any other ideas?

---

### Post by homicidalpossum on 2008-09-30
> **mikewhatever said:**
> It's odd, I expected the graphics driver would be there. Can you open Applications->Accessories->Terminal and post the output of the following:
.
Just wondering what driver is in use.
I am guessing my graphics driver isn't working as I cant enable any desktop graphics options so cant get the funky cube and stuff lol. I read in the other threads that is is because of not having any graphics drivers...
Thanks for the help, here is the text

chris@Mr-Wiggles:~$ cat /etc/X11/xorg.conf 
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
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by homicidalpossum on 2008-10-01
Bump, cant get compiz to work either so cant use the 3d desktop graphics sizzle.

---

### Post by doas777 on 2008-10-01
Interesting. there's no driver listed under the Device section. I've never seen that before. could you post your xorg.log file?

---

