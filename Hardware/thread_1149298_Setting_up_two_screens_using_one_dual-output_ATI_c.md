---
title: "Setting up two screens using one dual-output ATI card, with kubuntu 9.04"
date: 2009-05-05
forum: Hardware
---

### Post by Eagle-Owl on 2009-05-05
Hi Guys, 

I have just installed kubuntu 9.04 on some machine in the office. I have a dual output ATI card (ATI Radeon 7000/VE) and two big screens on the wall. I need to setup the system to use the two screens as one big desktop. the screens are identical, with maximum res. 1024x768. 
running xradnr always shows that VGA-1 is connected and VGA-0 is not connected (although both screens are physically connected). 
Now, I have found out that i need to do the following: 

xrandr --addmode VGA-0 1024x768
xrandr --output VGA-0 --mode 1024x768 --right-of VGA-1

This seems to be working, as the second screen (supposedly VGA-0) immediately comes up showing the wallpaper (although, black&white !!), and makes the two screens as one big desktop.
 
with this I still have two problems: 

1- this setting does not stick, and i have to do it each time I restart the machine, or the x-server. 
2- Once it's done, I still cannot move objects from the first screen to the END of the second screen. It stops in the middle of the second screen, exactly like hitting an invisible wall. After a lot of trying, I found that I only need to go to k-menu->settings->display , and soon this opens, the magic happens and the problem disappears without actually doing anything at all inside the display settings. 

Have anyone encountered such issue ?
How can I save xrandr setting, so I do not need to run them each time I restart the machine ?
and why does that invisible-wall issue happens ?

I appreciate any help.

---

