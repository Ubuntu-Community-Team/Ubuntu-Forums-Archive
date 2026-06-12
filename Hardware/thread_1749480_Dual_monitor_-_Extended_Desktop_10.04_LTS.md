---
title: "Dual monitor - Extended Desktop 10.04 LTS"
date: 2011-05-04
forum: Hardware
---

### Post by gaurab on 2011-05-04
Hi, 

I have been trying to setup dual monitor (DVI and VGA) with extended desktop without success. The most I can achieve is my DVI monitor working fine with the VGA monitor showing a blank (faint glow) screen.

My computer is on a network and I am not the admin (so, no root privilege).

Graphics card: ATI 
lspci gives:
VGA compatible controller: ATI Technologies Inc Device 68f9

The max resolution for the DVI monitor is: 1920x1080
The max resolution for the VGA monitor is: 1280x1024

The xorg.conf shows
```

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 3200 1080
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```
I used "xrandr" to set up the dual display. (followed [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("this tutorial"))
```
$ xrandr --output DVI-0 --mode 1920x1080 --pos 0x0 --output VGA-0 --mode 1280x1024 --pos 1920x0
```
Output from:
```
$ xrandr -q
``` 
is
```
Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 3200 x 1080
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 connected 1280x1024+1920+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  

```


Thank you for reading this post.

---

