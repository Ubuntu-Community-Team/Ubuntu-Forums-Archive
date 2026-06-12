---
title: "ATI Mobility Radeon 9600 M10 VESA Screen resolutoin with Karmic"
date: 2009-11-10
forum: Hardware
---

### Post by tropico on 2009-11-10
Hi all

I'm updating an old laptop (Packard Bell EasyNote R7725) to Karmic. And I'm facing some problems with the ATI video card.

My test to have a working X server

[LIST]
[*]It seems that the card is not supported by the "official" ATI driver anymore.
[*]The free driver (ati/radeon) frezze X at boot. 
[*]VESA driver works but in standard resolution ( 1024x768 ).
[/LIST]

I'd like to be able to set resolution to 1280x800 (max supported by the screen).I do not need any 3D acceleration

Here is a copy of my xorg.conf file with my tests


```
Section "Monitor"
        Identifier      "Configured Monitor"
        ModeLine        "1280x800" 69 1280 1296 1336 1408 800 800 803 816 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth    24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Module"
        Load    "dri"
        Load    "GLcore"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "vesa"
EndSection

```

Here is a little snip of the X log file (I can post the complete file if it helps)

```

...
(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.91 Hz
(II) VESA(0): Not using mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.91 Hz
(II) VESA(0): Not using mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
(II) VESA(0): Not using built-in mode "400x300" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
...
```

Thanks for help

Edit: 

I just try with xrandr with no success:

$xrandr --newmode "1280x800" 69 1280 1296 1336 1408 800 800 803 816 +hsync +vsync
$xrandr --addmode default 1280x800
$xrandr --output default --mode 1280x800
xrandr: Configure crtc 0 failed

I also tried using gnome interface with error : "Could not set the configuration for CRTC 256"

Edit2: The maximum screen resolution seems to be detected correctly.
$ xrandr -q
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1280 x 800
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   1280x800       60.1

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
[See if this by chance helps](http://ubuntuforums.org/showthread.php?t=1320785)

---

### Post by rhythmiccycle on 2009-11-10
I had this same problem and I just fixed it, now I want to help others, because I know how much it sucks.

I might be able to help.

what is the out put of this code:

```

cvt 1280 800

```

---

### Post by tropico on 2009-11-11
Hi rhythmiccycle

```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```

I just try that modeline with xrand rcommandsand I have the same error :"Could not set the configuration for CRTC 256"

Thanks

---

### Post by tropico on 2009-11-11
HI ST3ALTHPSYCH0,

Thanks forthe link, I'll try to look at that idea later today

---

### Post by rhythmiccycle on 2009-11-11
> **tropico said:**
> Hi rhythmiccycle

```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```

I just try that modeline with xrand rcommandsand I have the same error :"Could not set the configuration for CRTC 256"

Thanks

did you do it like this?:

```

xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync

```

then type

"xrandr" to  get the name of your monitor,

ex mine is VGA1, when I type xrandr it say this

```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3  
   640x480        59.9  
   1280x1024_60.00   59.9* 

```

after you get the name of your monitor use it in these lines, (i'm using VGA1, your monitor's name maynot be the same)

```

xrandr --addmode VGA1 1280x1024_60.00

```

and finally you can change to resolution with this code
```

xrandr -s 1280x1024

```

The only problem I still have is that I need to run those 3 lines of code everytime I reboot. but at least its out of 800x600.


when you do those lines does it still say, "Could not set the configuration for CRTC 256"?

---

### Post by tropico on 2009-11-11
Yes, I have that error...

If you want to save the xrandr config, you can add your xrandr command in a file saved in /etc/X11/Xsession.d/ 

Thanks

---

### Post by tropico on 2009-11-11
Hi I FOUND the Solution !!

[http://lists.freedesktop.org/archives/xorg-driver-ati/2009-January/007806.html](http://lists.freedesktop.org/archives/xorg-driver-ati/2009-January/007806.html)

Actually there is a problem with radeon driver and XOrg 7.4 which cause X to crash.

To use radeon driver with "ATI Mobility Radeon 9600 M10"

If you are already set to "radeon", then add the following under "Device"
Option            "AGPMode"          "1"

Thanks all for help

PS: No Need to disable DRI. It works with full 3D acceleration.

---

