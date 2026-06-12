---
title: "Gigabyte GTX 260 resolution problems"
date: 2014-10-17
forum: Hardware
---

### Post by tejes2 on 2014-10-17
Hardware:
MSI 945GCM7F
Intel Core 2 Duo E7400 slightly overclocked in BIOS from 2,8GHz to 3004MHz
Gigabyte GTX260OC 896MB GDDR3
2x2GB Kingmax DDR2 RAM of which only 3,2GB is used due to 32 bit chipset
Acer AL1716 monitor with 1280x1024 maximum resolution on VGA port

I had an x86 install of Lubuntu 13.10 (with kubuntu, ubuntu, and xubuntu desktops installed as well, just to try them out) besides Windows 7 on my machine. Mainly I use windows, but I like Linux too, so every now and then I booted it up, and played around. I can't remember when it occurred first, but from a time (most probably after an update, because I installed them regularly), I couldn't set the resolution higher than 1024x768. When I booted up Windows, it said that there are two monitors connected, which is not true. I just disabled the second one, and windows worked fine.
But I couldn't make anything in Lubuntu, so just not used it for a time.
A few days ago I wanted to get a Linux distribution working because of my university studies, so I decided to wipe off the existing Lubuntu, and installed Ubuntu MATE 14.10 beta 64 bit (because I like the classic Gnome look from 10.04 which was the first Linux I tried).
The problem hasn't gone away though. After some googling, I installed the nvidia-340 driver from the PPA xorg-edgers. With that, it now detects two monitors, just like Windows, and the resolution can go up to 1152x864 or even 1360x768, which is kinda odd.

xrandr says:
> Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192
VGA-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-I-0 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
The video card only has 1 VGA, 1 DVI, 1 HDMI slot and only the VGA is connected.

EDIT: Tried this without success:
> tejes@TejesBuntu:~$ sudo xrandr --newmode "1280x1024_60.0" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
tejes@TejesBuntu:~$ sudo xrandr --addmode VGA-0 "1280x1024_60.0"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30




I know that I am using a beta and non-official flavour of Ubuntu, but this happened in Lubuntu 13.10 too, and MATE is not so far from the others. I also know that this is most likely a hardware failure, but if Windows could somehow manage it, I hope that Ubuntu also can.

---

