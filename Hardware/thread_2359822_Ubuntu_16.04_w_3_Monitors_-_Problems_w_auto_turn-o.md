---
title: "Ubuntu 16.04 w/ 3 Monitors - Problems w/ auto turn-off and wallpaper changes"
date: 2017-04-28
forum: Hardware
---

### Post by pf49 on 2017-04-28
I just recently purchased a 4K monitor, originally intending to replace one of my current monitors, but I figured that I would try a 3-monitor setup. I am having two problems with this setup.

1. Monitors will not automatically turn off as before when the "Turn screen off" option is used. They will turn off, then turn back on, then turn off (mostly, sometimes).
2. Wallpaper on the 4K monitor is automatically resized and reoriented when waking from the automatic turn off and cannot be fixed using the Appearances tab in Settings.

Video card is a Radeon HD7850. It has two DVI ports, one HDMI, and two mini-Displayport. Ubuntu version is 16.04.1 running 4.4.0-75 kernel. 

Monitors are:
1. 28" Acer CB281HK running at 3840x2160 @60Hz, normal orientation, connected through one of the card's mini-DP ports, using a mini-DP to DP adapter (included with video card) to use the DP cable included with the monitor.
2. 22" Dell 2208WFP running at 1680x1050 @60Hz, vertical orientation, connected through DVI cable.
3. 22" Dell 2208WFP running at 1680x1050 @60Hz, vertical orientation, connected through DVI cable.

The 4K monitor is in the center with the two Dells flanking it on either side.

A fuller explanation of what's happening is that I set the "Turn screen off" to 10 minutes to save power. After ten minutes the screens will turn off. 30 seconds later they will turn back on, with the wallpaper on the 4K screen reoriented to vertical, and much smaller (I'm assuming 1050x1680 on the 4K screen). Then after another ten minutes the screens turn off again, except that the right hand-side Dell will have the launcher icons running along the left edge of the screen (I have them set to run on the bottom) with the rest of the screen black. Sometimes, for instance if I have a spreadsheet open, the spreadsheet will automatically be resized to full screen after ten minutes and the monitors won't turn off. With the wallpaper, going to the Appearances tab in settings shows it still running at 3840x2160 even though it clearly isn't. Opening the current wallpaper in Image Viewer, right-clicking, and selecting "Set as Wallpaper" does not change the resolution, it still remains at 1050x1680, vertically oriented. I have to select another wallpaper, which will then fill the screen, then change back to the original wallpaper. 

I tried installing the AMD GPU Pro drivers, version 17.10, but that didn't change any of this behavior. 

When I remove one of the Dell monitors and just run the 4K with one Dell everything works fine. The two monitors turn off at 10 minutes as they're supposed to and stay off, and the wallpaper remains at 4K on the 4K monitor when I wake it back up. It's only with three monitors that things start messing up. 

Worst case scenario I'll just deactivate the auto turn-off and turn the monitors off manually when I leave the computer, or just run two monitors, but it would be nice to have all three working properly. Any hints as to possible solutions would be much appreciated.

---

### Post by pf49 on 2017-04-28
The output of xrandr is as follows, in case that helps:

```

Screen 0: minimum 320 x 200, current 5940 x 2160, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 connected primary 3840x2160+1050+0 (normal left inverted right x axis y axis) 621mm x 341mm
   3840x2160     60.00*+  30.00    30.00    24.00    29.97    23.98  
   1920x1080     60.00    50.00    59.94    30.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      59.81  
   1152x864      75.00  
   1280x768      59.87  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
HDMI-A-0 disconnected (normal left inverted right x axis y axis)
DVI-I-0 connected 1050x1680+4890+0 left (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050     59.95*+
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
DVI-D-1 connected 1050x1680+0+0 left (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050     59.95*+
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  


```

---

### Post by pf49 on 2017-04-28
I appear to have fixed the auto turn-off feature by plugging the 4K monitor into DisplayPort-0 rather than DisplayPort-1. All three monitors will now turn off automatically when they're supposed to. The 4K monitor for some reason cycles through its possible inputs before turning off, so maybe it was expecting the turn-off command from DP-0 rather than DP-1 and seeing that DP-1 was still plugged in decided to turn the monitor back on. Who knows, but at least that was an easy fix. 

The wallpaper issue appears to have been the result of the placement of the monitors. After multiple attempts at solutions and multiple logouts and restarts, it appears that the wallpaper is now stable and won't resize on its own. Setting up the 4K monitor as the left-most monitor in Displays seems to have taken care of the problem. That may actually be a better setup for my work purposes than flanking the 4K with two smaller monitors. So I will go ahead and mark this as solved.

---

