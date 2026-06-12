---
title: "Using xorg.conf to keep dual monitor setup after boot"
date: 2010-10-21
forum: Hardware
---

### Post by petersfreeman on 2010-10-21
**Background**

When I was using Ubuntu 10.04, I had relied totally on the OS to detect and setup the the two displays, my main monitor(LCD) and a TV (LCD).  

After every reboot, it would have reverted to having the same image in both my monitor and TV and both my monitor and the TV would have the same lowest common denominator resolution (TV).

I needed to set it up the way I wanted by accessing the menu: System--->Preferences-->Monitors and change the setup by:
[LIST=1]
[*]Un-check "Same image in all monitors"
[*]Set the resolution of my main monitor
[/LIST]

It was a bit of a pain, but as I only needed to boot this computer (my wife's) about once a week, it was tolerable.

**Problem One**

I recently upgraded Ubuntu to 10.10 (Maverick Meerkat) and found that now I was not getting the virtual screen needed to set my main monitor to its maximum resolution. 

**Software**
[LIST]
[*]Ubuntu Release 10.10 (Maverick Meerkat)
[*]Kernel Linux 2.6.35.22 Generic
[*]GNOME 2.32.0
[/LIST]

**Hardware**

[LIST]
[*]Gateway with AMD Phenom 2 - X4
[*]ATI Radeon
[*]Samsung SyncMaster P2250 LCD Monitor
[*]Sanyo LCD-32E3 LCD TV
[/LIST]

**Available Screen Resolutions**

*Main monitor*

Screen 0: minimum 320 x 200, current 3280 x 1080, maximum 3280 x 1200
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+   50.0  
   1776x1000      60.0 +   50.0  
   1600x1200      60.0  
   1680x1050      60.0     50.0  
   1400x1050      60.0     50.0  
   1280x1024      60.0     50.0  
   1440x900       59.9     50.0  
   1280x960       60.0     50.0  
   1360x768       60.0  
   1280x800       60.0     50.0  
   1152x864       60.0     50.0  
   1280x768       59.9     50.0  
   1280x720       60.0     50.0  
   1024x768       60.0     50.0  
   1152x648       60.0     50.0  
   800x600        60.3     56.2     50.0  
   720x576        50.0  
   720x480        59.9     50.0  
   640x480        60.0     50.0  

*TV*

CRT2 connected 1360x768+1920+312 (normal left inverted right x axis y axis) 930mm x 523mm
   1360x768       60.0*+
   1280x768       59.9 +
   1280x720       60.0 +
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        60.0

I checked the /etc/X11/xorg.conf file and this is what had been built automatically by the installation:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    SubSection "Display"
        Virtual    2960 1200
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
```

I could see that to build the virtual display size, it had chosen the monitor display mode that had the largest Y dimension and used that for its X dimension and added it to the largest display mode for the TV. 

1600x1200 + 1360x768 = 2960x1200.

As I needed a virtual screen that covered the maximum horizontal **and** vertical dimensions of both monitors, I needed a virtual screen of 3280x1200.

I changed the section in the file /etc/X11/xorg.conf:

```
    SubSection "Display"
        Virtual    2960 1200
    EndSubSection

```
 to read

```
    SubSection "Display"
        Virtual    3280 1200
    EndSubSection

```
rebooted and after setting it up the way I wanted:

System--->Preferences-->Monitors and change the setup by:
[LIST=1]
[*]Un-check "Same image in all monitors"
[*]Set the 1920x1080 for my main monitor
[/LIST]

Apply-->Keep this configuration.

This problem was SOLVED.

**Problem Two**

Now I am back to the way it was before the upgrade from Ubuntu 10.04 to 10.10.  What I would like to do is to configure the /etc/X11/xorg.conf file so that after a re-boot, I do not need to set up up again.

I would like to have:  

[LIST]
[*]Setup so that the images that show in the *Monitor Preferences* window show **Monitor** and **TV** instead of **Unknown** and **Unknown**.
[*]The "Same image in all monitors" unchecked
[*]The Monitor set to 1920x1080 resolution
[*]The TV set to 1360x768 resolution
[/LIST]

While it is a secondary desire, it would be nice to position the two monitors in the virtual display so that the TV is to the right (the default) of the Monitor and it either lines up horizontally with the top or the bottom of the Monitor.

**Steps Taken**

I have added more information to the /etc/X11/xorg.conf file so it now reads:

```
Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Section "Monitor"
    Identifier    "Monitor"
    VendorName    "SamSung"
    ModelName    "SyncMasterP2250"
EndSection

Section "Monitor"
    Identifier    "TV"
    VendorName    "Sanyo"
    ModelName    "LCD-32E3"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device    "Default Device"
    DefaultDepth    24
    Monitor    "Monitor"
    Monitor    "TV"
    SubSection "Display"
        Virtual    3280 1200
    EndSubSection
EndSection

Section    "ServerLayout"
    Identifier    "Home Layout"
    Screen    "Default Screen"
EndSection

```

I'm not sure if this will work and I am also concerned that it will screw things up.

I have been reading the man pages for xorg.conf and while I understand that I need to bind the monitors to the screen in some way, I am not sure how to do this task.

What I am confuse about is where to bind the two monitors.  Near the end of the xorg.conf man pages, an example of the setup for multiple monitors is given:

```
       Here is an example of a ServerLayout section for a dual headed configuration with two mice:

           Section "ServerLayout"
               Identifier  "Layout 1"
               Screen      "MGA 1"
               Screen      "MGA 2" RightOf "MGA 1"
               InputDevice "Keyboard 1" "CoreKeyboard"
               InputDevice "Mouse 1"    "CorePointer"
               InputDevice "Mouse 2"    "SendCoreEvents"
               Option      "BlankTime"  "5"
           EndSection

```

Here they create two screens and bind the monitors outside of the virtual display.  I'm confused about the best way to go about this.

Could someone enrich my understanding of xorg.conf and how it should be setup for my hardware.

Thank you,

Peter Freeman

---

### Post by petersfreeman on 2010-10-21
**UPDATE**

By clicking the Make Default button in the *Monitor Preference*s window, I have solved part of *Problem Two*.  It now retains the settings of having "Same Image in all monitors" unchecked and it remembers the resolution that I want for both my monitor and TV.  This part of Problem Two is SOLVED.

By clicking the Make Default button also solved the positioning need that I had as a secondary desire.  This part is SOLVED

The remaining thing I would like to do is:

[LIST]
[*]Setup so that the images that show in the Monitor Preferences window show Monitor and TV instead of Unknown and Unknown.
[/LIST]

Any ideas?

Thank you,

Peter Freeman

---

### Post by petersfreeman on 2010-10-21
QUIRK

Now when I reboot, the initial logon screen is on my TV (in another room), however if I blindly hit enter to select the top user in the list, then blindly enter the password and hit enter, it continues booting up and my monitor has all the panels showing while the TV does not (which is how it should be).

It seems that although after boot-up is complete, my monitor (on the left) is considered the default monitor and thus displays all my panels, however, the TV is considered the default monitor during boot-up and displays the logon screen.

Any clue to this behaviour?

Thank you,

Peter Freeman

---

