---
title: "Two Monitors – Incorrect Resolution"
date: 2019-05-20
forum: Hardware
---

### Post by West Swan on 2019-05-20
Hello.

I have two Viewsonic VX2235WM monitors and a brand new GT710 graphics card.  Computer running Lubuntu 16.04

I have setup an extended display using ArAndR with the DVI-D-1 as active (and primary) and the VGA-1 as active.

This is not persisting though as when I restart the computer the VGA-1 is duplicating the DVI-D-1 and I have to open ArAndR and drag VGA-1 to the right again to extend it.   

That is not the biggest problem though as it is so easy to do.



**The biggest problem is with the resolution:  **

The DVI-D-1 monitor if plugged in by itself has the correct resolution of 1680 x 1050

The VGA-1 monitor if plugged in by itself has a resolution of 1024 x 768 which I can correct with a .xprofile file.  Thanks to DuckHook for explaining to me how to do this and that it is probably due to the monitor not reporting proper EDID information.

However, when both monitors are plugged in at the same time they each have a resolution of 1024 x 768 which I can&#8217;t fix.


What I have attempted thus far using LXTerminal is:


1. Generated a file onto the      desktop with the results of CVT: 

```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz

Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

```

2. Entered: 
```
xrandr --newmode "1680x1050_60.00" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

3. Entered: 
```
xrandr --addmode VGA-1 1680x1050_60.00


```

4. Entered: 
```
xrandr --output VGA-1 --mode 1680x1050_60.00


```
 
 
When I do this the VGA-1 monitor has the correct resolution and I can use ArandR to set the DVI-D-1 to the correct resolution also.  This doesn&#8217;t survive a restart.



To make the changes permanent I created a .xprofile file using leafpad and saved to the user directory that contains Documents, Pictures etc.


```
#!/bin/bash

xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-1 1680x1050
xrandr --output VGA-1 --mode 1680x1050

```
However upon restarting I get:

```
Error found when loading /home/user/.xprofile:


X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 140 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 35
Current serial number in output stream: 35

As a result the session will not be configured correctly.  
You should fix the problem as soon as feasible.

```
Funnily enough after clicking ok to that message the VGA-1 resolution is in fact fixed but the DVI-D-1 is still 1024x768  until I again go into ArAndR again and set it manually.



Please note I also tried adding _60.00 to the .xprofile ie replaced the two end lines which were 1680x1050 with 1680x1050_60.00 but get the same error.   



I think if I can get this .xprofile right then the two monitors will have the correct resolution?



Can anyone help?


Regards,

Paul

---

### Post by West Swan on 2019-05-20
Or perhaps even if there was some kind of executable file I could double click on once the desktop appears which:

a.  Changed ALL monitor resolutions to 1680 x 1050 and

b. Set VGA-1 as the extended display.


That is probably not possible I know :-)

---

