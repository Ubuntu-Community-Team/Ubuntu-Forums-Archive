---
title: "800x600 Max Resolution Problem"
date: 2009-05-13
forum: Hardware
---

### Post by Vigh on 2009-05-13
Hi, I am running Ubuntu 9.04 Jaunty, with EnvyNG-QT Nvidia version96 drivers, I know that the screen resolution can go higher the 800x600 but for some reason I am limited to 800x600 screen res after installing the drivers, any help appreciated. Anthony Vigh

The machine is a TOSHIBA LAPTOP- P4 mobile 2.0Ghz, 256MB RAM, 120GB HDD, dedicated mobile nvidia n graphics card 64mb

---

### Post by tuxwrench on 2009-05-14
I had a similar problem and here is what I think is the real problem.
The name of your Nvidia graphics card is different from what ubuntu is reporting, resulting in it giving you the default VESA settings which is 800x600.

Things to do:
1. Check out what is the exact model name of your Nvidia graphics card and list it down on the piece of paper.
2. Go to this [link]("http://packages.ubuntu.com/intrepid-updates/nvidia-glx-96") and cross check the name of your graphics card to the name listed on the jaunty nvidia-graphics-drivers 
3. Look for the name of the card which matches the most with your card. 
4. Open Terminal and type [FONT="System"]sudo gksu gedit /etc/X11/xorg.conf[/FONT]
5. Here is my sample of my xorg.conf which I edited

[FONT="System"]



Section "Device"
#	Identifier "nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)" [COLOR="Blue"] *this is what was reported by lspci so i had to change it[/COLOR]
	[COLOR="SeaGreen"]Identifier	"GeForce4 MX Integrated GPU"[/COLOR]
	Driver "nvidia"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
#	Device		"nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)"
	[COLOR="SeaGreen"]Device		"GeForce4 MX Integrated GPU"[/COLOR]
	[COLOR="SeaGreen"]DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "640x480" "800x600" 	
	EndSubSection[/COLOR]
# I also had to add this subsection in
	Option	"AddARGBGLXVisuals"	"True"
EndSection

[COLOR="SeaGreen"]Section "Module"
	Load	"glx"
EndSection[/COLOR]
[/FONT]


[COLOR="Red"]Warning: you need to also research about your monitor configuration if this doesn't work, and if it doesn't work... well do a restart, press ESC before grub loads and go to the recovery mode, select xfix and reboot, it will revert you back to start... keep on trying [/COLOR]

More help [here]("http://ubuntuforums.org/showthread.php?t=83973")

---

