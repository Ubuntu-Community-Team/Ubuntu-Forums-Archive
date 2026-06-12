---
title: "Monitor STOPPED working at 2560x1440"
date: 2014-06-02
forum: Hardware
---

### Post by tye2 on 2014-06-02
I have a Monoprice 27" IPS-Zero-G Slim Monitor, Model PID10509. Using my motherboard's on-board graphics to drive it. Motherboard is Asus Z87-A.

I set up this system about two months ago and it has worked perfectly, displaying 2560x1440, until two ago. Now, after reboot, it maxes at 1680x1050. I am using DVI-D port and cable.
 I am not a Linux pro. The only thing I am aware of changing before the problem is the installation of Pipelight to enable Silverlight for Netflix. Since then, I allowed Ubuntu to upgrade itself from 13.10 to 14.04.

I have tried to fix problem Google searching.
Using: cvt 2560 1440 (tried both 30 and 60 for refresh)
xrandr --newmode "2560x1440"  [output from cvt]
xrandr --addmode HDMI1 2560x1440
xrandr --output HDMI1 --mode 2560x1440
This only makes the screen black out and return to 1680x1050 mode. It show that 2560x1440 mode exists after I add via command line, but this option disappears after reboot (and never actually enters 2560x1440).

Additionally, I have tried deleting my ~/.config/monitors.xml file.

At this point, I am at the limit of my Linux sleuthing skills. There is probably important information that I didn't know to add; please ask. Any help appreciated.

---

### Post by zeke3 on 2014-07-01
I have the same problem. I'm running it on a Gigabyte Brix Pro i5 though. No luck getting it back up to full resolution.

---

### Post by tgalati4 on 2014-07-02
It's possible that the display (Monoprice tend to be cheaper construction) cannot handle the higher frequencies required to drive the display.  Try using different cables.  Do a google search on your exact model and see if others are having problems.  Find someone with a Mac and try to get full resolution.  If you can't then you can be reasonably sure that the monitor has developed a fault.

One last test.  Wrap it in a large plastic bag and put it in the refrigerator with the cable attached.  Leave it for a couple of hours to cool down.  Pull it out, leave the bag on (to prevent condensation) and plug it in and see if it will display full resolution.  If it works, then leave it for a while and see what happens when it heats up.

---

### Post by squakie on 2014-07-03
I understand the refrigerator deal - cool it down.  Just on a larger scale than when we use freeze spray on a component to find out that is falling at temparature.   However, given what some refrigerator can actually cool to, it might be wise to be sure you are also not outside on the low end of the recommended operating tempature range for you monitor.  Normally excessive heat is more of a problem than being too cool, but you never know.

---

