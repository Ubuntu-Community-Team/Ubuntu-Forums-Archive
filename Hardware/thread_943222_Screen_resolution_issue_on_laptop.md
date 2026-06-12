---
title: "Screen resolution issue on laptop"
date: 2008-10-10
forum: Hardware
---

### Post by Radiotic on 2008-10-10
I have a question about display settings and graphics drivers on my Asus A8J laptop (NVIDIA Geforce 7600) installed with Hardy. I installed it for the first time last week, so yeah, I'm a total noob. Considering this fact, I'll just list out what happened and what I've done. 

I've been using Hardy for about a week with no display problems until yesterday when I booted up to a message that said my display type and graphics card couldn't be detected, I selected the appropriate options and proceeded only to find that the max screen res was 800x600, despite having chosen higher options before logging in. 

I think it might go as high as 1280x800, but 1024x768 would be fine. 

I tried fixing it myself as per this [guide]("https://help.ubuntu.com/community/FixVideoResolutionHowto"), but after logging back in, I'm back on 800x600 (or lower sometimes) with no option to change. I haven't tried every solution in the guide yet but will shortly if no other ideas are posted. 

Any help would be appreciated. Cheers. 

Here's a bit of my xorg.conf file for reference. 
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

---

### Post by WWSmith36 on 2008-10-10
You can use a simple tool to reset you video setting.

Open a terminal from the menu Applications-> Accessories-> Terminal, and type

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk
```

You will be ask for your password, type it, you won´t see the cursor move. Hit enter.

Then to configure your monitor resolution:

```
sudo displayconfig-gtk
```

You can select your monitor from the list or add it by using the .inf file from driver disk or download. If the screen is too large to access buttons at the bottom, ALT+ LEFT CLICK will allow you to move the window.

Hope this helps

---

### Post by Radiotic on 2008-10-10
Thanks. Can't wait to try it, but just got sucked into another few hours of work away from my laptop. I'll give it a shot later and let you know how it went. Thanks again.

---

### Post by Radiotic on 2008-10-10
Works great. It took a few log offs to retain the settings. But it's taken ok now. Only problem is the log in screen is too big, the name entry section is kinda on the bottom right of the screen, and the options on the bottom left are off-screen. But, otherwise, all is well. 

Thanks for the help.

---

### Post by gliding4me on 2008-10-10
I have been having the same problem of a maximum screen resolution of 800 x 600 on an old Toshiba Laptop that can go to 1024 x 768.

Thanks to WWSmith36 for the help that lead to my solution.

My fix turned out to be quite easy in fact. After executing the command

sudo displayconfig-gtk

I selected "LCD Panel 1024 x 768" from the Model pull down menu.

I then ran the test, which didn't work.  However, I accepted the new setting, logged out and logged back in and all was resolved.  On reboot, the setting has been maintained also.

---

