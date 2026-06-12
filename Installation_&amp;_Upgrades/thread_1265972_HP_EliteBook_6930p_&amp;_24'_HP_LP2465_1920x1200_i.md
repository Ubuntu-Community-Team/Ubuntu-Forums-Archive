---
title: "HP EliteBook 6930p &amp; 24' HP LP2465 1920x1200 installation"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by andronus on 2009-09-14
Hello 
under Ubuntu my  24' HP LP2465 cannot have more than 1600x1200 so you need to do this:

-try to play with System->Preferences->Display you will see the dfault definition for your laptop screen & additional external screen.

-in console mode run:

**$lspci**
to know which video card you use
[CENTER] VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
[/CENTER]

then run 
**$gtf 1920 1200 60 -x**
that give you all the screen options for the 24 monitor

[CENTER] # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
[/CENTER]

**$xrand**
see the ouput, notice the HDMI/VGA/....here you got all available resolution available
trick is to add a new resolution

play these:
[B]xrandr --output LVDS --mode 1440x900
xrandr --newmode "1920x1200" 193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA 1920x1200
xrandr --output VGA --mode 1920x1200 --right-of LVDS
xrandr --addmode HDMI-1 1920x1200
xrandr --output HDMI-1 --mode 1920x1200 --right-of LVDS

#xrandr --output TV --off
#xrandr --output HDMI_1 --off[/B]

#check conf
**xrandr **

###################################
[LEFT]Screen 0: minimum 320 x 200, current 3360 x 1200, maximum 3360 x 1200
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   59.9  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 connected 1920x1200+1440+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      59.9  
   1600x1000      60.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1152x720       60.0  
   1024x768       75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)
###################################

[/LEFT]


you might need to plug your monitor to direct VGA replay then with preference->display...
in the end it was working ofr me

---

