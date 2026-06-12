---
title: "Login screen does not fit to monitor"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by verboten soul on 2009-05-03
UF ate my post.

Now I need to reenter it 3rd time:

When upgrading from 6.06 to 8.08 ( I know I am late, but I don't care being pioneer - and you'll see why shortly) I spent couple "interesting" hours reconfiguring xserver. NVidia nForce hated me until I stumbled upon EnvyNG, which of course saved my bacon - BIG THANKS to authors. But it was not all:

After I login all is peachy, but login screen is weird: input area for Login name and password are way down and right, so I cannot even see them (I enter values blindly and can login OK). How to fix it? I prefer GUI tools but I not afraid to edit xorg.conf if needs be. Here it is:

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection "Display"
        Depth    24
        Modes        "800x600@85"    "800x600@60"    "800x600@75"    "832x624@75"    "800x600@72"    "1024x768@85"    "800x600@56"    "1024x768@75"    "640x480@85"    "1024x768@70"    "640x480@75"    "1024x768@60"    "640x480@72"    "1024x768@43"    "640x480@60"    "1152x864@75"    "1280x1024@75"    "1280x960@60"    "1280x960@85"    "1280x1024@85"    "1280x1024@60"    "1280x960@75"    "1400x1050@60"    "1400x1050@75"    "1600x1200@65"    "1600x1200@60"    "1600x1200@75"    "1600x1200@70"    "1792x1344@60"    "1856x1392@60"    "1920x1440@60"    "2048x1536@60"
    EndSubSection
    Option        "AddARGBGLXVisuals"    "True"
    Defaultdepth    24
EndSection

Section "Screen"
    Identifier    "screen1"
    Device        "device1"
    Monitor        "monitor1"
    Option        "AddARGBGLXVisuals"    "True"
    Defaultdepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "NVIDIA GeForce2 Integrated (generic)"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
    Vendorname    "NVIDIA"
EndSection

Section "Device"
    Identifier    "device1"
    Boardname    "NVIDIA GeForce2 Integrated (generic)"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    1
    Vendorname    "NVIDIA"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Dell"
    Modelname    "Dell M992"
    Horizsync    30.0-96.0
    Vertrefresh    50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "monitor1"
    Gamma    1.0
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection


```BTW something strange is set up with Javascript on posting thread page: I have JS enabled for UF but disabled for all others and it wiped out my posts. Enabling Yahooapis helped, but why yahoo  should even know about what I do here?

---

### Post by verboten soul on 2009-05-03
bump? Anyone? Any better subforum to ask this?

---

### Post by donpedrodos on 2009-05-03
Looks like your resolution for GDM is incorrect.

One day snooping my filesystem, I found an interesting one line config file, wich stated very clear the GDM resolution.
So it looks like GDM is not taking the resolution from Xorg config, but has this one line config file with the resolution inside.

I was now trying to find this file in the filesystem, but was unable to find it at this moment.:(

Maybe someone else can confirm that this one line resolution file exists and where it is in the filesystem.

---

### Post by upchucky on 2009-05-03
K first you need to verify which version you are running, there is no 8.08

if it is 8.04, then this is the only way to set up nvidia properly.

Envy was never a fix all for nvidia, it was simply a workaround, and enabled almost everything possible, on future releases it breaks.

```
Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```


if it is 8.10, there are issues with it and nvidia, 8,10 was never a supported release, it is still beta.

If it is 9.04, i would be careful, although this is a long term release, there are many issues with it, search the boards for 9.04 threads, you will see what i mean.

---

### Post by verboten soul on 2009-05-04
My version is 8.04 LTS :blush: it just So rhymed with 6.06 :-)

---

### Post by verboten soul on 2009-05-07
self-answer: In section "Monitor" I commented out all modelines with overly-high resolution (more than 1200 lines).

Doh! It was so obvious. :-)

Thanks [upchucky]("http://ubuntuforums.org/member.php?u=269247") - your solution might help next struggler. I was almost there, commenting modlines I did not needed was good enough solution for me.

---

