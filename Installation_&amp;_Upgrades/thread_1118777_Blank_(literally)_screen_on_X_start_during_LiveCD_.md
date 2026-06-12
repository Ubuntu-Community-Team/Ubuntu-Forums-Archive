---
title: "Blank (literally) screen on X start during LiveCD install"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by sweetnsourbkr on 2009-04-07
I seem to have a unique problem with my system.

Gigabyte GA-MA78GPM-DS2H mobo
Gigabyte Radeon 4870 vid card
Disabled onboard HD 3200 video

Whenever I boot into the Intrepid LiveCD, the system loads but as soon as X attempts to start, I am greeted by either a blank white, or blank black screen.

This happens with two different monitors of different sizes.

I had this problem before I installed the 4870, but I was able to install using a smaller monitor with a standard 1280x1024 res.  With the 4870, it won't load the desktop, even if I enable and use the onboard video.  I'm going to try removing the 4870 board before starting tonight, but it seems to be a completely unecessary step since others don't have a problem starting X using a 4870 with the LiveCD.

Anything I'm missing here?

---

### Post by sweetnsourbkr on 2009-04-07
I've been able to install Intrepid using the alternate CD, but when X tries to start during the first boot, same problem crops up.  There seems to be a problem with the stock Radeon driver, but it worked before when I initially installed the 4870 board, and the system ran fine for a while.

Problems started when I attempted to install the newest Catalyst 9.3 driver from ATI for added functionality.  Worst mistake I ever made on this computer. :(

---

### Post by peakshysteria on 2009-04-07
How did you installed the latest driver? Have you looked at: [Ubuntu Jaunty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")?

---

### Post by sweetnsourbkr on 2009-04-07
Jaunty won't even start on this computer, so I'm not sure how applicable those instructions are.  

The initial install for the 4870 was on a fully running Intrepid install.  The system was running the FGLRX driver from ATI, and it was plug and play.  However, the LiveCD seems to have some diarhea when it comes to using the stock radeon driver with the 4870.  Strange, since others I've talked to don't seem to have any problems with their 4870.  I haven't been able to install the FGLRX driver on the LiveCD because I can't even get to the desktop!

My mistake was to use the .run file as-is, without making a package as per the instructions.

---

### Post by upchucky on 2009-04-07
remove the borked video install, start over, and since you have identified your mistake don't make the mistake again.

once you have a command line install working, you gonna have to manually experiment with the screen and resolution settings in the xorg.conf

if the live cd boots up to a gui, check it's xorg.conf and try the settings it uses on the actual installed os.

---

### Post by sweetnsourbkr on 2009-04-07
I'm already ahead of you, upchucky.  Thanks.  My problem is that the LiveCD/alternate GUIs will not start.  I have not been able to get the Fn consoles to work on Intrepid, perhaps it was a functionality that was removed with the last release.

---

### Post by elcman on 2009-04-07
This is something that I'm having a problem with. For some reason, I'm running into this with my crappy Intel onboard video. I'm curious if anyone could figure out what might be causing this.


Annoying... I tell ya. After getting into GDM it shows the two bars (top and bottom toolbar/taskbars) and then it shows a pure white background that I can't get past.

~~
Erik

---

