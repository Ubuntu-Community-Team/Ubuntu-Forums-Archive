---
title: "TC1000 natty install"
date: 2011-04-30
forum: Hardware
---

### Post by linuxlover42 on 2011-04-30
I have recently received an old Compaq TC1000 with a corrupted OS. I decided to install Linux on it and this old machine works better than windows ever did. I almost have all the original functionality back (I will post this if somebody can help me out) but it is missing one thing, the pen.

I found the proper driver (fpit) and was forced to install the beta for natty as maverick was incompatible with it. I then followed various instructions on these forums on modifications to my xorg.conf file and none of them worked. I finally decided to generate and xorg.conf file and add the code for the pen to it. This made a little progress as now whenever I touch the pen to the screen x promptly crashes. Here is my xorg.conf file, any help is appreciated. Thanks

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    InputDevice    "Configured Mouse"
    InputDevice    "Generic Keyboard"
    InputDevice    "Pen"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
    Load  "record"
    Load  "dri"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ImPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier "pen"
    Driver "fpit"
    Option "AlwaysCore" "on"
    Option "Device" "/dev/ttyS0" #ttyS0
    Option "BaudRate" "19200"
    Option "MaximumXPosition" "8600" # "6250"
    Option "MaximumYPosition" "6485" # "4950"
    Option "MinimumXPosition" "154"
    Option "MinimumYPosition" "110"
    Option "InvertY"
    Option "TrackRandR"
    Option "SendCoreEvents"
    Option "Button2" "3"
    Option "ReportingMode" "Scaled"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:0:5:0"
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "nv"
    BusID       "PCI:0:5:0"
EndSection

Section "Device"
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:0:5:0"
EndSection

Section "Device"
    Identifier  "Card3"
    Driver      "vesa"
    BusID       "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by linuxlover42 on 2011-04-30
So now, without much further ado, the instructions. This is currently a work in progress and I will be updating it untill I am done (It will hopefully be complete when someone helps me get the pen working). 

Also, this is not all my work, much of it has been adapted and edited from various places, most from these forums, so if you see your work here and would like a credit, please let me know (give me a link to your post though so I can make sure it is in fact your work).

Screen Rotation:

This is fairly simple, it merely involves making a script containing this code. And linking it to a panel custom applet launcher. (Note this requires xrandr to work.)

```
#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS-1|cut -b38-43`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
```
please note that if this does not work, type in xrandr -q --verbose in the terminal, identify the line that deals with your monitor, replace LVDS-1 with the name of your monitor, and replace 38-43 with the start and end bytes of the word normal (while your screen is in normal rotation). I also included a special icon I made for the screen rotation launcher, a purely aesthetic thing but it looks nice.

---

### Post by linuxlover42 on 2011-04-30
Hold it, is this the final version of  Natty, has that been released yet?:confused:

Edit: I installed the final version of Natty and I'm following a few leads on the pen and graphics drivers.

---

### Post by Learning2LikeLinux on 2011-05-06
I have been following your posts.  I have been trying to get the pen working in Natty on a TC1000 as well, but haven't gotten to far with it.  At one point, whenever I touched the pen to the screen, it actually would log me out.  Have your had similar behavior?

Also, your xorg.conf file is much longer and more complicated then others that I have seen posted.  Is there a reason for this?

Thanks for posting your results.  I hope that you are able to figure out the pen and graphics issues.  For now I am just going to stay with 10.04, because it is working for me.

---

### Post by linuxlover42 on 2011-05-07
favux is helping me out with this here [http://ubuntuforums.org/showthread.php?t=1751149](http://ubuntuforums.org/showthread.php?t=1751149). I will post the results once/if I meet with any success (considering favux's skill if there is a way to get this working he will find it)

---

