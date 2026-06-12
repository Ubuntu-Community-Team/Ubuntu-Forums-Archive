---
title: "*ubuntu 8.10 on laptop, how to use external monitor?"
date: 2008-12-13
forum: Hardware
---

### Post by elpenor23 on 2008-12-13
I'm using an old laptop that I occassionaly install Linux on just to play with. The last distro I used was Arch and I haven't used any Linux in some time. I'd like to use an external monitor in place of the laptop panel. I vaguely remember how to set up a dual display using Xinerama, but I have no idea how to do it with xrandr. I don't even want to. 

I'd like the OS to detect the presence of an external monitor and use it in place of the laptop display, without prompting. I thought I was comfortable editing Xorg.conf and init scripts, but I'm not clear on how things work with HAL handling most of the configuration.

Can someone provide straight forward instructions on configuring xubuntu to handle an external display? 

Here is the output of xrandr without any switches:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1600 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 359mm x 287mm
   1600x1024      60.2  
   1280x1024      60.0     60.0  
   1440x900       59.9  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        60.0     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

The monitor plugged into the only VGA out on the laptop is an LCD with a native resolution of 1280x1024. As far as I can tell, xrandr doesn't "see" it, since what it is listing as VGA 0 is clearly the internal display. 

Xorg.conf was automatically configured and reads as follows:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Not including lines/sections that were commented out, all of which are preceded by a comment reading:
# commented out by update-manager, HAL is now used


To sum up: I'd like to know how to configure Xorg.conf and/or xrandr and/or a startup script so that, when an external monitor is present, it is used as the primary and only display. I wouldn't mind the ability to run a dual display, but I'm primarily interested in switching between the external monitor and internal display depending on the presence or absence of the former.

Can anyone help me out?

Thanks!

PS The laptop is an old Dell D600 (near junk), if that matters.

---

### Post by linux_tech on 2008-12-14
Use this command to go back to external only:
```
xrandr --output LVDS --off
```

If you're using the laptop monitor only and the external monitor is plugged in and turned on (but not active), use this command:
```
xrandr --output VGA --same-as LVDS
```

Use this command to go back to laptop only:
```
xrandr --output VGA --off
```


This article explains more on using xrandr or xorg to regulate video choices. I like xrandr because it is dynamic, faster to troubleshoot and usually resolves issue faster.   
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

---

### Post by elpenor23 on 2008-12-14
Does this mean I don't need to configure a screen or device in xorg.conf? Using your instructions I am able to clone the laptop panel output to the external monitor and to switch to the external monitor. But when I switch it has the wrong resolution, when I try to set the proper resolution through the display GUI provided by xfce4, the various applets (like the panel) disappear, and sometimes xfwm seems to die. Other times, when I switch, the external monitor briefly displays a really distorted image before going to gray. The external monitor has a native resolution of 1280x1024 while the internal has a resolution of 1024x768. What more do I need to do to get this working?

Thanks for your help.

---

### Post by xscottx3 on 2008-12-14
If you are using nvidia drivers it is really simple. All you need to do is...

sudo nvidia-settings

And go to the monitor configuration tab, click detect, and then you are able to adjust things around to how you would like. Then save the xorg file (it will prompt you how) and log out and log back in and it should all be working correctly. You may have to alter resolutions if it does not detect them automatically.

This is how I got my laptop and TV synchronized. Hope it helps.

---

### Post by elpenor23 on 2008-12-14
unfortunately, I'm not using nvidia drivers but ATI.

---

