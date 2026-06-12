---
title: "Will Compiz work on dual screens?"
date: 2008-10-21
forum: General Help
---

### Post by pkjm17 on 2008-10-21
Hi,
I'm trying to use compiz-fusion and when I try to enable the 3d desktop effects it says something like "composite extension not available." I'm using dual screens with xinerama.1280x1024 for both. NVIDIA GeForce 6200 graphics card. On Ubuntu 8.

Let me know if you need any more information. Thanks for the help!

---

### Post by klange on 2008-10-21
Quick answer: In most cases, no.
Long answer: Depends on the maximum texture size your card supports. If your entire screen layout fits within that box, yes, but this is rarely the case, as the maximum texture size for most cards is 2048x2048.

I believe the 6200 has a maximum texture size of 2048x2048. Your layout is 2560x1024, so it will not fit.

We're looking into various ways to "fix" this.

(that and you're missing the composite extension in your X config)

---

### Post by MaxIBoy on 2008-10-21
I can't think of any way that Compiz wouldn't work on dual screens. EDIT: So I was wrong. Disregard that other stuff below. I'm not going to delete it because I may need to copy and paste it into another post to help someone else.

Try setting up your drivers with envy. Pull up a terminal (applications > accessories > terminal) and type this in:
```
sudo apt-get install envyng-gtk
```
Then type in your password. You won't see * for each letter you type, that's normal.

After that, it should appear in the applications > system tools menu. If it does not, pull up another terminal and type this in:
```
gksudo envyng
```



This will help you setup your drivers.

If that still doesn't work, type the following into a terminal:
```
compiz --replace
```
Then copy and paste the error message you get into a post here so we can see what's wrong.

---

### Post by blazercist on 2008-10-21
I use compiz on dual monitors with an Nvidia card, specifically the 9600GT, but the user WindowsSucks is correct the only real limitation is your video card's max texture size, and only in relation to your desired collective monitor resolution.

Twinview works perfectly, there are some problems if you want to run seperate X servers for each screen, but even the seperate X server problems are surmountable in some cases.

---

### Post by jerome1232 on 2008-10-21
I've thought xinerama only allowed 3d acceleration on one screen?

At any rate it does work with separate x screens, but you can't drag windows between them. I've had problems getting everything setup right (each screen is setup separately from the other and etc..)

---

### Post by blazercist on 2008-10-21
My experience with xinerama has been... less than acceptable.  Twinview works great and is essentially the same as xinerama.  I would suggest using the Propreitary driver by the way.  Please FOSS zealots don't knock my advice with the proprietary driver, it comes from personal experience.

---

### Post by fenian on 2008-10-21
Seperate x screens with compiz enabled works with no tweaking needed in Intrepid though in Hardy you probably will need to use the [menu fix]("http://ubuntuforums.org/showpost.php?p=5231933&postcount=70") and may have issues when using multimedia keys to control volume.

---

### Post by bodhi.zazen on 2008-10-21
I was going to say I have not had any problems with beryl or compiz with my dual monitors and either of two nvidia cards.

When using Twinview you get one big cube covering both screens. When using separate monitors you get a cube on each screen.

---

### Post by loomsen on 2008-10-21
Separate X-Screens here.

Actually one has no other choice if the screens have different resolutions... But I'd always prefer separate X-screens. TwinView as well as Xinerama are just workarounds imho.

The difference is basically where the Screens get connected to the server, which as well determines what is possible and what is not.

```

 ServerLayout "Layout0"
        |
        |--> Screen "Screen0"
        |       |
        |       |--> Monitor "Monitor0"
        |       |
        |       |--> Device "Videocard0"
        |       |
        |       |--> Options
        |
        |
        |--> Screen "Screen1"
        |       |
        |       |--> Monitor "Monitor1"
        |       |      
        |       |--> Device "Videocard1"
        |       |      
        |       |--> Options
        |     
        |
        |--> InputDevice "Keyboard0"
        |      
        |
        |--> InputDevice "Mouse0"
        |       
        |
        |--> InputDevice "Synaptics Touchpad"
        |      

    ServerFlags
        |
        |--> Option "Xinerama" "0"
    Extensions
        |
        |--> Option "Composite" "Enable"

```
Thats mine with separate X-Screens.

---

### Post by pkjm17 on 2008-10-22
> **loomsen said:**
> Separate X-Screens here.

Actually one has no other choice if the screens have different resolutions... But I'd always prefer separate X-screens. TwinView as well as Xinerama are just workarounds imho.

The difference is basically where the Screens get connected to the server, which as well determines what is possible and what is not.

```

 ServerLayout "Layout0"
        |
        |--> Screen "Screen0"
        |       |
        |       |--> Monitor "Monitor0"
        |       |
        |       |--> Device "Videocard0"
        |       |
        |       |--> Options
        |
        |
        |--> Screen "Screen1"
        |       |
        |       |--> Monitor "Monitor1"
        |       |      
        |       |--> Device "Videocard1"
        |       |      
        |       |--> Options
        |     
        |
        |--> InputDevice "Keyboard0"
        |      
        |
        |--> InputDevice "Mouse0"
        |       
        |
        |--> InputDevice "Synaptics Touchpad"
        |      

    ServerFlags
        |
        |--> Option "Xinerama" "0"
    Extensions
        |
        |--> Option "Composite" "Enable"

```
Thats mine with separate X-Screens.

Loomsen,
What are your screen resolutions for this?

---

### Post by loomsen on 2008-10-22
Attached my whole layout, my xorg in it too.

Somehow Opera doesn't get along to well with the attachement manager...

---

### Post by pkjm17 on 2008-10-23
I have this at the end of my xorg.conf. Is this correct?


Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "true"
    Option         "DAMAGE" "true"
EndSection

---

### Post by loomsen on 2008-10-27
Thats how mine looks too.

Like the name says, it's the extensions section. You may enable them, you don't have to. 

Your Xorg log will show you useful info.

```
cat /var/log/Xorg.0.log | grep EE
```
will show errors.

```
cat /var/log/Xorg.0.log | grep WW
```
will show warnings.

Adding the last section only won't make it work tho.

Your layout is more important, post your xorg.conf and I'll have a look at it if you still have problems.

---

### Post by pkjm17 on 2008-11-02
Here is my layout. I'm open to different screen resolutions...Which ever you think would work best.


nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
    Load           "GLcore"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Gateway"
    ModelName      "Gateway EV700B"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "WDE L1975NW"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
    ModeLine       "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
    ModeLine       "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway"
    HorizSync       31.5 - 68.7
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:2:9:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:2:9:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:9:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:9:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "800x600@85" "800x600@60" "800x600@75" "832x624@75" "800x600@72" "1024x768@85" "800x600@56" "1024x768@75" "640x480@85" "1024x768@70" "640x480@75" "1024x768@60" "640x480@72" "1024x768@43" "640x480@60" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-1: 800x600@60 +0+0; CRT-1: 800x600@56 +0+0"
# Removed Option "metamodes" "CRT-1: 1280x1024 +0+0; CRT-1: 800x600@56 +0+0"
# Removed Option "metamodes" "CRT-1: 1280x1024 +0+0"
# Removed Option "metamodes" "CRT-1: 1024x768 +0+0"
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 640x400 +0+0; CRT-0: 800x600@60 +0+0; CRT-0: 800x600@75 +0+0; CRT-0: 832x624@75 +0+0; CRT-0: 800x600@72 +0+0; CRT-0: 1024x768@85 +0+0; CRT-0: 800x600@56 +0+0; CRT-0: 1024x768@75 +0+0; CRT-0: 640x480@85 +0+0; CRT-0: 1024x768@70 +0+0; CRT-0: 640x480@75 +0+0; CRT-0: 1024x768@60 +0+0; CRT-0: 640x480@72 +0+0; CRT-0: 640x480@60 +0+0; CRT-0: 1152x864@75 +0+0; CRT-0: 1280x960@60 +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0"
# Removed Option "metamodes" "CRT-0: 1024x768 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "true"
    Option         "DAMAGE" "true"
EndSection

---

### Post by loomsen on 2008-11-02
Attached a file which should give you a good base to start off from.

Btw, you'll probably have to edit it here and there, nvidia-xconfig has a nice option... run it with

```

me@tiffany:~$ nvidia-xconfig -c ~/dualhead-xorg.txt -T
```

And it will take the file dzalhead.txt, parse it, and show the layout in a tree-view, and tell you bout errors while parsing.
```

    ServerLayout "Default Layout"
        |
        |--> Screen "Screen0"
        |       |
        |       |--> Monitor "Monitor0"
        |       |       |
        |       |       |--> VendorName "Gateway"
        |       |       |--> ModelName "CRT-0"
        |       |       |--> HorizSync  
        |       |       |--> VertRefresh  
        |       |       |--> Modeline "1280x1024@60" ...
        |       |       |--> Option "DPMS"
        |       |
        |       |--> Device "Videocard0"
        |       |       |--> Driver "nvidia"
        |       |       |--> VendorName "NVIDIA Corporation"
        |       |       |--> BoardName "GeForce 6200"
        |       |       |--> BusID "PCI:2:9:0"
        |       |       |--> Screen "0"
        |       |
        |       |--> Option "AddARGBGLXVisuals" "True"
        |       |--> Option "TwinView" "1"
        |       |--> Option "metamodes" "CRT-0: 1280x1024 +0+0"
        |       |--> DefaultColorDepth 24
        |
        |--> Screen "Screen1"
        |       |
        |       |--> Monitor "Monitor1"
        |       |       |
        |       |       |--> VendorName "Gateway"
        |       |       |--> ModelName "CRT-1"
        |       |       |--> HorizSync  
        |       |       |--> VertRefresh  
        |       |       |--> Modeline "1280x1024@60" ...
        |       |       |--> Option "DPMS"
        |       |
        |       |--> Device "Videocard1"
        |       |       |--> Driver "nvidia"
        |       |       |--> VendorName "NVIDIA Corporation"
        |       |       |--> BoardName "GeForce 6200"
        |       |       |--> BusID "PCI:2:9:0"
        |       |       |--> Screen "1"
        |       |
        |       |--> Option "AddARGBGLXVisuals" "True"
        |       |--> Option "TwinView" "1"
        |       |--> Option "TwinViewXineramaInfoOrder" "CRT-0, CRT-1"
        |       |--> Option "metamodes" "CRT-1: 1280x1024 +0+0"
        |       |--> DefaultColorDepth 24
        |
        |--> InputDevice "Keyboard0"
        |       |
        |       |--> Driver "kbd"
        |       |--> Option "XkbRules" "xorg"
        |       |--> Option "XkbModel" "pc105"
        |       |--> Option "XkbLayout" "us"
        |       |--> Option "CoreKeyboard"
        |
        |--> InputDevice "Mouse0"
        |       |
        |       |--> Driver "mouse"
        |       |--> Option "Protocol" "auto"
        |       |--> Option "Device" "/dev/psaux"
        |       |--> Option "Emulate3Buttons" "no"
        |       |--> Option "ZAxisMapping" "4 5"
        |       |--> Option "CorePointer"
        |


    ServerFlags
        |
        |--> Option "Xinerama" "1"

me@tiffany:~$ 

```

Thats your layout, for example :) 

Check out my sig on xorg...

---

### Post by ad_267 on 2008-11-02
I have no problems running compiz with TwinView.

---

### Post by Arl on 2008-11-03
I've had issues with Ibex. I was running the test version and it was working fine, but now it locks up when I switch desktops w/ Desktop Cube. I tried reinstalling the Nvidia Drivers ( I have a GeForce 9600 GSO card). Any suggestions?

---

### Post by cprofitt on 2008-11-03
I am using an Nvidia 8800GTS 320 with two 1280x1024 monitors and compiz works fine.

---

### Post by loomsen on 2008-11-04
> **Arl said:**
> I've had issues with Ibex. I was running the test version and it was working fine, but now it locks up when I switch desktops w/ Desktop Cube. I tried reinstalling the Nvidia Drivers ( I have a GeForce 9600 GSO card). Any suggestions?

Do you have a group video and are you as your user in this group?

check 
```
groups
```

If not, you have to create one. Default values for nvidia are too restrictive, so it could as well be possible that group video is there, but has only 0600 permissions, so only root can access it.

The group should have GID 044, and permissions 0660

Try and add this to the bottom of your xorg:
```

Section "DRI" 
     Group "video" 
     Mode 0660 
EndSection

```

This should grant access to your device.If you don't mind other users to have access too you may change 0660 to 0666.

---

### Post by earthpigg on 2008-11-04
> **Arl said:**
> I've had issues with Ibex. I was running the test version and it was working fine, but now it locks up when I switch desktops w/ Desktop Cube. I tried reinstalling the Nvidia Drivers ( I have a GeForce 9600 GSO card). Any suggestions?

i had the same problem (and in Mint-64 which is based on 8.04-64bit, too... but not 8.04 64 bit)... using the 177 driver fixed it for me :)

---

### Post by Arl on 2008-11-04
> **earthpigg said:**
> i had the same problem (and in Mint-64 which is based on 8.04-64bit, too... but not 8.04 64 bit)... using the 177 driver fixed it for me :)

I reinstalled the 17 7drivers. I'll look into what loomsen said

---

### Post by Arl on 2008-11-06
fixed it. I had to add the groups line to my xorg file. Thanks

---

### Post by loomsen on 2008-11-06
:guitar:

---

### Post by borlosky on 2008-11-12
sure will work on dual screens....but how about working on 6 screens..... well just check this out: [http://ubuntuforums.org/showthread.php?t=884161]("http://ubuntuforums.org/showthread.php?t=884161")

---

### Post by loomsen on 2008-11-12
If you get 2 separate X-Screens working it's no big thing to add another one. Threat title should be ...dual+ screens... more accurate.

---

### Post by DouglasAWh on 2008-11-15
Twinview worked fine for me with compiz in Gutsy but Ibex broke it. I've got Twinview working again and compiz works...but without window decoration. I've had to fix desktop effects on both my laptop and desktop and among some other issues am becoming very frustrated.  I don't think this is an X issue, but here's my xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview Radius-73"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro4 750 XGL"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

