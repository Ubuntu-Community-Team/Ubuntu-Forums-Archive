---
title: "I cant install new themes"
date: 2008-10-25
forum: General Help
---

### Post by biowerks on 2008-10-25
Maybe im doing it wrong but I got Ubuntu because I saw the videos on youtube with the cool way to switch between desktops with the cube and all the really nice looking fades and effects. So I get Ubuntu, I dont have a username and password so I have to get into the command line and get a username and password then the screen size is stuck on 800x600 I edit my xorg.conf file (I am not at all familiar with linux or editing code) then I have to get a flash plugin but I cant get that from the normal sources so I have to figure that out...I am surprised that I havent given up yet. Now comes the time where I want to get a theme and try to figure out that cube thing and I keep downloading themes and getting a message saying that this doesnt seem to be a valid theme. OK I have Ubuntu 8.04 and have not done anything other than fix the screen, get flash, and get username and PW. I am going to [http://www.gnome-look.org](http://www.gnome-look.org) and downloading stuff from there. I have seen on youtube that compiz stuff works but I cant get anything out of it. Can someone Please help me. I am really frustrated.

and what is this kubuntu, xobuntu and so on?

---

### Post by Nuetouch on 2008-10-26
I to have seen the kool things on youtube about ubuntu, and I even put a video on youtube asking for help. No help yet. Although I have been using ubuntu for 2 months little at a time, and have came a long way. After installing on 3 different computers it was ok, but no effects. So, I built a used p4 2.5 mhz w/128 nvidia card and 384 ram, and presto, it came to life..Everything looks sharper and moves way faster, and the advanced windows effects are active, it is worth while to stick it out, and now I've installed Suns Virtual box and after 2 tries, installed windows XP Pro. However, I am stuck where you are. I only managed to install one theme out of about ten. None seem to work or install correctly. I did watch tutorials on youtube and they were helpfull, but I still can't get them to install. On the other hand, I did install a package that allows you to enable the 3d cube and other effects, I am currently in the process of finding out how to activate the cube, it is there because i saw all the new settings after I installed the package. As I learn more I'll post the info, keep going its worth it...

---

### Post by eternalnewbee on 2008-10-26
Hi guys. Could you please mention your system specifications, so the people here can be able to help you out?
If you don't know how to do that, you could install an application called Sysinfo. Go to Main Menu > Add/Remove Applications, and in the search bar type sysinfo, tick the to install. After typing your password, it will be installed. Once the installation is finished you can find Sysinfo in Main Menu > System Tools. There you will find detailed information about your soft- and hardware. These are my specs, as an example:

Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

It is important for the people here to know this, because, for example not all graphic cards can handle 3D acceleration, which enables you to get these special effects up and running.

---

### Post by eternalnewbee on 2008-10-26
Nuetouch here's a link to a tutorial that might be intersting for you:
[http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10](http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10)

---

### Post by Nuetouch on 2008-10-26
I tried that link, and it aint no different than what I've been doing, and it still won't work. I must be missing something small, or maybe need to install a different package....Hmmmmm

---

### Post by fredbird67 on 2008-10-26
OK, to address your main question about why you can't install themes, sometimes a theme creator will put MULTIPLE themes in the same *.tar.gz (or whatever) file. in which case, you will need to right-click on that file and click "Extract Here" -- it may have other *.tar.gz (or whatever) files in it, too.  It may also have a folder in it as well, in which case you just open it and view the contents of the folder, which may have the *.tar.gz (or whatever) file(s) you're really looking for.

Second, you mentioned being stuck on an 800x600 screen resolution.  I would bet that that's probably because your video card hardware is not compatible with Hardy Heron or Intrepid Ibex.  I'm planning to have my wife get me some different hardware for Christmas so that I can go to screen resolutions beyond 800x600, because I had the very same problem with Hardy and couldn't figure out why for the longest time, so I'm replacing my motherboard over Christmas break (I work at a college here in St. Louis and have a couple weeks off, BTW).  Until that time, I'm still running Ubuntu 7.10, which is the last version of Ubuntu that supports my graphics card.

Third, you asked what Kubuntu and Xubuntu are.  These are versions of Ubuntu that feature alternate desktop environments, namely KDE and Xfce, respectively.  With Linux, unlike Windows, you're not limited to just one graphical user interface (or GUI for short, which is pronounced "gooey").  Ubuntu, by default, uses the GNOME desktop environment, although if you wish to experiment, you can also download KDE and Xfce to Ubuntu as well, and then when you log in, just select which desktop environment you want.  In fact, this is explained in greater detail at [http://www.whylinuxisbetter.net/items/window_managers/index.php?lang=](http://www.whylinuxisbetter.net/items/window_managers/index.php?lang=)

Hope this helps! :-)
Fred in St. Louis, MO USA

---

### Post by biowerks on 2008-10-26
Thanks for the responses 

Ill get my hardware info up asap. (im on my windows partition now). 

fredbird67

You can get past that 800x600 screen resolution pretty easily. (I am FAARRRR from an expert when it comes to linux but I have learned a few things since I got into it.) First try to right click on applications and click on edit menus then click on other and add screens and graphics then goto that window and add your monitor from the list. My monitor wasnt on that list so I just kinda made it up... I have an eMachines computer and I know that it is made by gateway so I added a gateway monitor with the model numbers closest to my model and chose the resolution that I wanted and restarted and now Im in 1024x768 just like I wanted.If you dont have that option you can specify your own screen resolution by editing your etc/x11/xorg.conf file. mine looks like this now.

```
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

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1730 R9"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

if you look at yours next to mine you should be able to pick out the differences and eidt accordingly. If it gives you trouble saving then close out gedit and in the terminal screen type. ```
gksudo gedit /etc/X11/xorg.conf
``` and then edit and you will be able to save.

I compiled all of that info from differnet people on this forum and some of my own experimentation but it did work for me.

---

