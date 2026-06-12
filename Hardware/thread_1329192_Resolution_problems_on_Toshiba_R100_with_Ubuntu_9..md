---
title: "Resolution problems on Toshiba R100 with Ubuntu 9.10"
date: 2009-11-17
forum: Hardware
---

### Post by Lennart K on 2009-11-17
After a smooth installation process of the Ubuntu 9.10 on my Toshiba R100 I have only one problem. The system generates a maximum 800x600 resolution while the native resolution is 1024x768. The small size of the screen makes it almost impossible to use. The VGA compatible controller is a Trident Microsystems Cyberblade XP4m32 (rev 91).
Please, give me a clue!! 
 
:???:

---

### Post by realzippy on 2009-11-17
Try:

**cvt 1024 768 60**

and post the output please...

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> Try:
 
**cvt 1024 768 60**
 
and post the output please...
 
 
Post it where? I'm a beginner..

---

### Post by realzippy on 2009-11-17
**cvt 1024 768 60**

run this command in a terminal,It should give a new modeline,which
you should post here in the forum...



edit:
To open a terminal,press Alt+F2 and type:

**gnome-terminal**

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> **cvt 1024 768 60**

run this command in a terminal,It should give a new modeline,which
you should post here in the forum...



edit:
To open a terminal,press Alt+F2 and type:

**gnome-terminal**


Thanks - the response is;

~$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

and then...?

---

### Post by realzippy on 2009-11-17
Terminal:

**xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync**

then:

**xrandr --addmode VGA1 1024x768_60.00**

then (test that mode):

**xrandr --output VGA1 --mode 1024x768_60.00**


If it should work you can make it permanent.I am not shure if your output is VGA1,but we will see...

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> Terminal:
 
**xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync**
 
then:
 
**xrandr --addmode VGA1 1024x768_60.00**
 
then (test that mode):
 
**xrandr --output VGA1 --mode 1024x768_60.00**
 
 
If it should work you can make it permanent.I am not shure if your output is VGA1,but we will see...
 
When executing the first xrandr command I just get the prompt again (but no error reported)
Executing the second command givs me the response **xrandr: cannot find output "VGA1" **i tried VGA, VGA0 and VGA2 with the same result!

---

### Post by realzippy on 2009-11-17
what does

**xrandr -q**

say?

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> what does

**xrandr -q**

say?


The response is;

~$ xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x118)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz

---

### Post by realzippy on 2009-11-17
So please try **LVDS**  instead of VGA1:

[B]xrandr --addmode LVDS 1024x768_60.00
[/B]


?

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> So please try **LVDS**  instead of VGA1:

[B]xrandr --addmode LVDS 1024x768_60.00
[/B]


?

Sorry, but same result;

~$ xrandr --addmode LVDS 1024x768_60.00
xrandr: cannot find output "LVDS"

I found the name to be "default" and I managed to do the addmode command without getting an error. testing the output comman gave however;
:~$ xrandr --output default --mode 1024x768_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)

---

### Post by realzippy on 2009-11-17
Do you have a xorg.conf file?

Terminal:

**gedit /etc/X11/xorg.conf**

please post it if it is not empty.If so,run:

[B]sudo dpkg-reconfigure -phigh xserver-xorg
[/B]

Still empty?



Just got a visitor,that means I am offline for max. 1 hour.,but will be back,sorry.
meanwhile you could also try given lines without any output (no VGA/LVDS)...

---

### Post by Lennart K on 2009-11-17
> **realzippy said:**
> Do you have a xorg.conf file?
 
Terminal:
 
**gedit /etc/X11/xorg.conf**
 
please post it if it is not empty.If so,run:
 
**sudo dpkg-reconfigure -phigh xserver-xorg**
 
 
Still empty?
 
 
Yes, it is still empty!!

---

### Post by KeLa on 2009-11-17
Here is copy of my R100 xorg.conf file.
```

Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics" "AlwaysCore"
EndSection

Section "Files"
    RgbPath      "/usr/X11R6/lib/X11/rgb"
    FontPath   "/usr/lib/X11/fonts/misc/"
    FontPath   "/usr/lib/X11/fonts/TTF/"
    FontPath   "/usr/lib/X11/fonts/Type1/"
    FontPath   "/usr/lib/X11/fonts/CID/"
    FontPath   "/usr/lib/X11/fonts/75dpi/"
    FontPath   "/usr/lib/X11/fonts/100dpi/"
    FontPath   "/usr/lib/X11/fonts/local/"

EndSection

Section "Module"
    Load  "dbe"
    Load  "extmod"
    Load  "fbdevhw"
    Load  "glx"
    Load  "record"
    Load  "freetype"
    Load  "type1"
    Load  "synaptics"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "IMPS/2"
    Option        "Device" "/dev/mice"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "yes"
EndSection

Section "InputDevice"
   Driver "synaptics"
   Identifier "Synaptics"
   Option "Device" "/dev/input/mouse0"
   Option "Protocol" "auto-dev"
   Option "LeftEdge" "130"
   Option "RightEdge" "840"
   Option "TopEdge" "130"
   Option "BottomEdge" "640"
   Option "FingerLow" "7"
   Option "FingerHigh" "8"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "110"
   Option "EmulateMidButtonTime" "75"
   Option "VertScrollDelta" "20"
   Option "HorizScrollDelta" "20"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "1.10"
   Option "AccelFactor" "0.030"
   Option "EdgeMotionMinSpeed" "200"
   Option "EdgeMotionMaxSpeed" "200"
   Option "UpDownScrolling" "1"
   Option "CircularScrolling" "1"
   Option "CircScrollDelta" "0.1" Option "CircScrollTrigger" "2"
   Option "SHMConfig" "on"
   Option "Emulate3Buttons" "on"
 EndSection
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Toshiba TOS5082"
    DisplaySize  240    180
    HorizSync    31.0 - 48.0
    VertRefresh  50.0 - 70.0
    Option        "dpms"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "vesa"
    VendorName  "Videocard vendor"
    BoardName   "VESA driver (generic)"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Group        0
    Mode         0666
EndSection

```

This works on my machine.

---

### Post by Lennart K on 2009-11-17
> **KeLa said:**
> Here is copy of my R100 xorg.conf file.
```

Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics" "AlwaysCore"
EndSection

Section "Files"
    RgbPath      "/usr/X11R6/lib/X11/rgb"
    FontPath   "/usr/lib/X11/fonts/misc/"
    FontPath   "/usr/lib/X11/fonts/TTF/"
    FontPath   "/usr/lib/X11/fonts/Type1/"
    FontPath   "/usr/lib/X11/fonts/CID/"
    FontPath   "/usr/lib/X11/fonts/75dpi/"
    FontPath   "/usr/lib/X11/fonts/100dpi/"
    FontPath   "/usr/lib/X11/fonts/local/"

EndSection

Section "Module"
    Load  "dbe"
    Load  "extmod"
    Load  "fbdevhw"
    Load  "glx"
    Load  "record"
    Load  "freetype"
    Load  "type1"
    Load  "synaptics"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "IMPS/2"
    Option        "Device" "/dev/mice"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "yes"
EndSection

Section "InputDevice"
   Driver "synaptics"
   Identifier "Synaptics"
   Option "Device" "/dev/input/mouse0"
   Option "Protocol" "auto-dev"
   Option "LeftEdge" "130"
   Option "RightEdge" "840"
   Option "TopEdge" "130"
   Option "BottomEdge" "640"
   Option "FingerLow" "7"
   Option "FingerHigh" "8"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "110"
   Option "EmulateMidButtonTime" "75"
   Option "VertScrollDelta" "20"
   Option "HorizScrollDelta" "20"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "1.10"
   Option "AccelFactor" "0.030"
   Option "EdgeMotionMinSpeed" "200"
   Option "EdgeMotionMaxSpeed" "200"
   Option "UpDownScrolling" "1"
   Option "CircularScrolling" "1"
   Option "CircScrollDelta" "0.1" Option "CircScrollTrigger" "2"
   Option "SHMConfig" "on"
   Option "Emulate3Buttons" "on"
 EndSection
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Toshiba TOS5082"
    DisplaySize  240    180
    HorizSync    31.0 - 48.0
    VertRefresh  50.0 - 70.0
    Option        "dpms"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "vesa"
    VendorName  "Videocard vendor"
    BoardName   "VESA driver (generic)"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Group        0
    Mode         0666
EndSection

```This works on my machine.

When I try to create an xorg.conf file I cannot save it on /etc/X11/. I get the message **Could not save the file /etc/X11/xorg.conf.** You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. In the 9.10 version there is no conf-file to start with!

????

---

### Post by KeLa on 2009-11-17
Use following command from terminal:
sudo gedit /etc/X11/xorg.conf
Enter your password when asked.
Then you can save the file after editing it.
Then restart X or reboot computer.

---

### Post by Lennart K on 2009-11-17
[SIZE=5]**The problem is solved!**[/SIZE]

with 

sudo gedit /etc/X11/xorg.conf (requesting my password)

I managed to create the xorg.conf file proposed by KeLa and after restart it really worked directly!

Thanks a lot for the help to both to KeLa and realzippy - I learned a lot in the process!

---

