---
title: "xrandr and tv out disp;ay doesn't work anymore"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by sfielder on 2007-12-17
Hi I am running dell Inspiron e1405 with intel 945gm graphics card,and gutsy. I was trying to enable my S-video port. I was able to get a signal on my tv by restarting X no problem, but it wasn't a great resolution etc. (it was cloning my 1440x900 resolution)  So, I started looking around and found some info on the xrandr command. I played around with that to turn the TV output off and on without restarting X, and it worked great until .... I broke something....

I think I was trying to change the resolution on the tv output, when something happened. What I have now is very strange. It seems that the hardware thinks a tv is attached when there is none. when I boot the computer into gutsy (I still have a vista install that I haven't reformatted yet) the splash screen shows up as normal, when I get to the login prompt the normal screen resides in a lower resolution 'box', if you will. I can login and my screen goes blank. At this point I can use the 'CRT/LCD' hardware switch to re-enable the laptop screen, but the resolution is wrong. The bagkground is the right size, but the taskbar is in the middle of the screen just like before i broke things. so I open a terminal and use xrandr to turn TV off and every thing is sort of OK.  until I have to reboot.

I have tried dpkg-reconfigure server-xorg , and restoring a backup of my xorg.conf but no avail.

What makes me think something weird is going on is that when I put in the live cd to try to backup my files and reinstall the I was greeted with the same display settings on the live desktop (taskbar floating in space) and sure enough, xrandr --output TV --off fixed it. 

Last I booted up the other partition on my drive and vista thinks the tv is plugged in as well.....

I am stumpped. I probably should have read a little more about what I was doing before I did any configuring, but this is how you learn right? 

At this point I am not sure that a reinstall will fix my problem. Can someone please help me?

thanks

---

### Post by sfielder on 2007-12-17
does anyone know if it is possible that xrandr wrote to the video bios?

when I run xrandr with the -q option it detects the following:

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1920 x 1440
VGA disconnected (normal left inverted right)
LVDS connected 1440x900+0+0 (normal left inverted right) 304mm x 190mm
   1440x900       60.0*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected (normal left inverted right)
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

the TV is NOT connected and those are not the correct refresh settings anyway.
It also doesn't matter if the cable is plugged in or not, the output is the same.

---

### Post by mocha on 2007-12-22
I've never used "xrandr" so I don't know anything about it.  I can tell you that in Feisty I set up my system to have 2 X screens.  The main one is my VGA monitor and the second one is my television hooked via S-video.  This way I can run fullscreen videos/DVDs on the television while using my computer on the VGA.  The television is to the "right of" the monitor, so I move my mouse off screen to the right and it goes to the TV.  I had to do a lot of hacking of the xorg.conf to get this to work properly.  xorg-reconfig and the nvidia-settings utility never worked properly for me.  Here is my xorg.conf, this is NOT one size fits all, you're going to need to hack it to work with your system but hopefully it's a start for you, PM me if you have any questions:

```



Section "ServerLayout"
    Identifier     "Layout0"
     Screen      0  "Screen0" 0 0
     Screen      1  "Screen1" RightOf "Screen0"
     InputDevice    "Generic Keyboard"
     InputDevice    "Configured Mouse"
EndSection

Section "Files"
     FontPath        "/usr/share/fonts/X11/misc"
     FontPath        "/usr/share/fonts/X11/cyrillic"
     FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
     FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
     FontPath        "/usr/share/fonts/X11/Type1"
     FontPath        "/usr/share/fonts/X11/100dpi"
     FontPath        "/usr/share/fonts/X11/75dpi"
     FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
     Load           "bitmap"
     Load           "ddc"
     Load           "extmod"
     Load           "freetype"
     Load           "glx"
     Load           "int10"
     Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
								#Television
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
								#LG VGA Analog
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L1960TR"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024_75 +0+0"
    Option         "UseEDID" "true"
    Option         "Coolbits" "1"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "enable"
EndSection

```

---

### Post by sfielder on 2008-01-18
Thanks, I have been without My laptop, so no posting.  Talked with Dell and they determined that I fried my graphics card/m-board (under warranty YAY!). So that is all fixed. One question I still have is: is it possible that I did something to the motherboard/ graphics card to create this problem? If anyone knows or knows who to ask, let me know or (better yet) point them here.

Sam

---

### Post by mocha on 2008-01-22
Did you overclock the processor or memory?  I've never heard of a GPU board failing.  Perhaps they don't vent their cases properly.

---

### Post by www.rzr.online.fr on 2008-05-18
may this page help :

[http://rzr.online.fr/q/xrandr](http://rzr.online.fr/q/xrandr)

---

