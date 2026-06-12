---
title: "XRANDR &quot;Can't Open Display&quot;"
date: 2012-03-27
forum: Hardware
---

### Post by 3li4.b on 2012-03-27
Hi all, I've a very odd issue with my laptop and a VGA monitor.
The laptop is a HP Pavillion ZV5000EA (lubuntu 11.10) with ATI mobility radeon 9000IGP in it, but without it's original lcd display because is broken so I torn it out and I'm using it with a VGA monitor.
I was used to use it with an LG Flatron L1910B and I was working awesomely.
Yesterday I changed the monitor with a Samsung SyncMaster 793s and it stopped working completely. I mean, just the video output, because the rest is still working. It has a ssh and vnc server in it and remotely I could see that the system was not crushed (and working). I checked xrandr in a console and it said "Can't open display". I tried to reconfigure xserver, but it still cannot open the display. I also noticed that, booting, it doesn't even show the bios splash screen nor the grub screen so I cannot choose the kernel to boot. Once booted the monitor shows a moving message with "Hz ??"
And now the **ODD** part. I plugged the laptop back to its beloved LG Flatron L1910B and it was working (as usual), than I unplugged it and plugged into the Samsung and **it is working! WHY!?** This is the output of xrandr:
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 312mm x 234mm
   1280x1024      60.0*+
   1024x768       85.0 +   75.1     70.1     60.0  
   1152x864       75.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      59.9 +
   1400x1050      60.0  
   1280x1024      59.9* 
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```
Does anybody have experienced this behaviour, or have an idea? I really don't know what to do, I googled like hell usuccessfully. Right now I'm using the LG monitor as a kick-start and I feel stupid.

Thanks guys.

---

### Post by rmil on 2012-03-27
**Now when everything works fine keep the copy of your working xorg.conf somwhere else for safety**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

If you come into same situation:
Try to find Horizontal and Vertical sync values for your monitor over google. Then edit xorg.conf. In most situations it is done this way:
```
sudo nano /etc/X11/xorg.conf
```Now edit the Monitor section and put right minimal and maximal values for Horizontal and Vertical sync.

The problem is that when you plug different monitor new values are put into xorg.conf. Sometimes monitors are detected ok sometimes are not.

---

### Post by 3li4.b on 2012-03-27
THANKS rmil!!
I didn't have any xorg.conf to keep in safe and I made up a new one, blending the details of the graphic card and the monitor randomly found with google in this xorg.conf
```
Section "Device"
        Identifier "ATI Radeon"
        Driver "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "Monitor"
Identifier	"Configured Monitor"
Vendorname	"Samsung"
Modelname	"Samsung SyncMaster 793S/793V/CM173G"
Horizsync	30-71
Vertrefresh	50-160
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
Gamma	1.0
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Configured Monitor"
Device	 "ATI Radeon"
Defaultdepth	24
SubSection "Display"
Depth	24
Modes	 "1024x768@70"	"1024x768@60"	"1024x768@75"	"1024x768@43"	"1024x768@85"	"1152x864@75"	"832x624@75"	"1280x960@60"	"800x600@60" "1280x1024@60"	"800x600@85"	"1400x1050@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72" "640x480@60"
EndSubSection
EndSection
```
Now it works as it should! Thanks agaig, I thought that with xrandr there was no xorg.conf to set :)

Cheers

---

