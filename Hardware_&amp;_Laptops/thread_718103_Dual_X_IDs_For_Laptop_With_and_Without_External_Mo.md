---
title: "Dual X IDs For Laptop With and Without External Monitor"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by cmnorton on 2008-03-07
I have a goal for the use of a Thinkpad T61p, and I need some advice on how to achieve my goals. I need to use this system in both an external monitor (KVM switch with Thinkpad docking station) and in standalone mode. 

I spent a week getting the T61p working in the KVM environment. Basically, I had to change the graphics driver to vesa. The Thinkpad was set to VGA+LCD output. In this configuration, the Thinkpad only displays to the external monitor. 

Today, I got a shock. I needed to take my laptop to a meeting (away from the external monitor environment). It would not boot with usable graphics. I changed the BIOS output to Thinkpad LCD, and still there was no success. I eventually got the laptop working in the docking station again. The conclusion I came to was I could not use the vesa driver for the laptop's internal display, but I could not get the nvidia driver working with the external display. 

I have not removed any of the /etc/X11/xorg.conf saved files. I concluded that xorg.conf.99 was the original xorg.conf that was generated when I first installed Ubuntu and before I tried to get the laptop integrated into the external monitor environment. I will have to try this out to see if this configuration (using the nvidia driver) will work when the laptop is not configured with an external monitor.

IBM Thinkpad support told me to configure a second monitor. However, when I tried that, System --> Administration --> Screens and Graphics would not let me configure a second monitor. Clicking on OK would had no action; nothing happened.

Is this best thing for me to keep two xorg.conf files and when I want to switch boot into recovery mode and make the switch? Does xrandr play a role in creating the second display, and which is the second display, if the laptop's native screen is not displaying?

---

### Post by jamesrl on 2008-03-08
I have a similar setup; I have a laptop that I sometimes hook up to an external monitor at home (1680x1050 that I use to the left of laptop), and an external monitor at work (1280x1024 that i use to the right of my laptop).  I am using ubuntu 7.10 (Gnome).

I basically switch between configurations using xrandr (1.2 from Gutsy) with only one xorg.conf configuration (the only changes made to it are adding Virtual lines to each display subsection:
```

        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
                Virtual         3360 1050
        EndSubSection

```
(note this works for the lower resolution external monitor as well).
Then I create a few scripts to automate the xrandr command (so I can switch back and forth with single clicks).

Now, I prefer having a different configuration of panels based on whether I have one monitor or two monitors.  [Right now I have a single panel at the top of each monitor that both has a main menu, task bar (listing all open programs on that monitor), clock, etc.]  I acheived this by configuring my panels to the way I like them with both monitors open and then saving them into a XML file (which I put in ~/settings/panel_home_screens.entries ... you can save as a file wherever you want) using gconftool-2 as follows:

```

gconftool-2 --dump /apps/panel > ~/settings/panel_home_screens.entries

```
I also switch back to one monitor mode and save my panels the way I like them, and dump the settings into a file ~/settings/panel_one_monitor.entries

Then my script to load two monitors goes as (saved into an executable shell script I call home_screens.sh):

```

#!/bin/bash

### this part is to test whether the external monitor is connected
myline=`xrandr | grep VGA | grep -v disconnected`
 echo $myline
if [[ "$myline" != "" ]]
then
 echo "ext monitor connected"

### LVDS is laptop screen, VGA is external monitor
### this is the xrandr line that load it
  `xrandr --output LVDS --auto && xrandr --output VGA --left-of LVDS --auto`

### this changes the panel configuration to the two monitor setting
  gconftool-2 --load ~/settings/panels_home_screens.entries
###  this reloads the gnome panel (gnome automatically reloads panels after being killed)
  killall gnome-panel
## this  is just the gnome-network applet that needs to be restarted after killall gnome-panel
  nm-applet &

else
 echo "VGA disconnected"
 `xrandr --output LVDS --auto`
  gconftool-2 --load ~/settings/panels_one_screen.entries
  killall gnome-panel
  nm-applet &
fi

```
You can then create a new custom application launcher for the shell scripts (don't forget to make them the bash script executables or call them as "bash ~/local/bin/home_screens.sh" or whereever you saved them.


I also made separate similar scripts for my work configuration, my external monitor only config (for watching movies), my laptop only config, cloned config.

---

### Post by cmnorton on 2008-03-09
> **jamesrl said:**
> I have a similar setup; I have a laptop that I sometimes hook up to an external monitor at home (1680x1050 that I use to the left of laptop), and an external monitor at work (1280x1024 that i use to the right of my laptop).  I am using ubuntu 7.10 (Gnome).

I basically switch between configurations using xrandr (1.2 from Gutsy) with only one xorg.conf configuration (the only changes made to it are adding Virtual lines to each display subsection:
```

        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
                Virtual         3360 1050
        EndSubSection

```(note this works for the lower resolution external monitor as well).
Then I create a few scripts to automate the xrandr command (so I can switch back and forth with single clicks).

Now, I prefer having a different configuration of panels based on whether I have one monitor or two monitors.  [Right now I have a single panel at the top of each monitor that both has a main menu, task bar (listing all open programs on that monitor), clock, etc.]  I acheived this by configuring my panels to the way I like them with both monitors open and then saving them into a XML file (which I put in ~/settings/panel_home_screens.entries ... you can save as a file wherever you want) using gconftool-2 as follows:

```

gconftool-2 --dump /apps/panel > ~/settings/panel_home_screens.entries

```I also switch back to one monitor mode and save my panels the way I like them, and dump the settings into a file ~/settings/panel_one_monitor.entries

Then my script to load two monitors goes as (saved into an executable shell script I call home_screens.sh):

```

#!/bin/bash

### this part is to test whether the external monitor is connected
myline=`xrandr | grep VGA | grep -v disconnected`
 echo $myline
if [[ "$myline" != "" ]]
then
 echo "ext monitor connected"

### LVDS is laptop screen, VGA is external monitor
### this is the xrandr line that load it
  `xrandr --output LVDS --auto && xrandr --output VGA --left-of LVDS --auto`

### this changes the panel configuration to the two monitor setting
  gconftool-2 --load ~/settings/panels_home_screens.entries
###  this reloads the gnome panel (gnome automatically reloads panels after being killed)
  killall gnome-panel
## this  is just the gnome-network applet that needs to be restarted after killall gnome-panel
  nm-applet &

else
 echo "VGA disconnected"
 `xrandr --output LVDS --auto`
  gconftool-2 --load ~/settings/panels_one_screen.entries
  killall gnome-panel
  nm-applet &
fi

```You can then create a new custom application launcher for the shell scripts (don't forget to make them the bash script executables or call them as "bash ~/local/bin/home_screens.sh" or whereever you saved them.


I also made separate similar scripts for my work configuration, my external monitor only config (for watching movies), my laptop only config, cloned config.

Thanks. I'll give this a whirl.

---

