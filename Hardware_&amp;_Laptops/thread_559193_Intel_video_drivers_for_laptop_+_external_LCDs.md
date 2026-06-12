---
title: "Intel video drivers for laptop + external LCDs"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by ekirby on 2007-09-24
First, these forums have been invaluable, so thanks to all you knowledgeable people who are so generous with your advice!

This issue is similar to several others already posted, but the solutions given aren't quite what I need.

With the help of these forums, I have gotten 1680 x 1050 resolution to work on my external widescreen LCD.  I got this to work by installing the xserver-xorg-video-intel package.  It works wonderfully as long as the external monitor is plugged into the laptop.  As a bonus, the laptop screen is a clone of the external screen (at the same overly large resolution, but who's counting?).

Unfortunately, if the laptop is booted without the external screen plugged in, the login screen shows up with fonts that are so enormous that I can see only a small fraction of the screen.  I can see enough to click my username and type my password, but just as soon as it tried to login, it returns immediately to the overly large login screen.

The solution posted for this problem so far is to (re)install xserver-xorg-xserver-i810, which automatically uninstalls xserver-xorg-xserver-intel.  However, it doesn't seem that 1680 x 1050 resolution is possible with the former.

To summarize,

xserver-xorg-video-i810: able to use laptop at native 1200 x 800 resolution, but not external LCD
xserver-xorg-video-intel: able to use external LCD at native 1680 x 1050 resolution, but not laptop by itself

machine: HP Pavilion dv4170
video chipset: Mobile 915GM/GMS/910GML Express Graphics Controller
system: Feisty (Ubuntu 7.04)

Here are the relevant sections of my /etc/X11/xorg.conf.  I have tried the drivers "i810" and "intel" with both xserver-xorg-video-i810 and xserver-xorg-video-intel.

```

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     30-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

I appreciate any help you can offer in getting my laptop to work standalone and the external LCD to work at its native resolution with the same driver and xorg configuration.  But even if I never get it to work, you guys sure are helpful!

Evan

---

### Post by ekirby on 2007-09-26
Okay, I've partly figured out the solution.  In order to make the GDM login fonts the correct size, I modified the X server login settings:

System -> Administration -> Login Window
Security Tab
Configure X Settings ... button
command text box: add  -dpi 96

Unfortunately, as soon as I log in, I get kicked back to the login screen.  I have made a new post for this problem:
[URL="http://ubuntuforums.org/showthread.php?p=3432075#post3432075"]
http://ubuntuforums.org/showthread.php?p=3432075#post3432075[/URL]

Thanks!
Evan

---

