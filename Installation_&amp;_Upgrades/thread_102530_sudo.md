---
title: "sudo"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by mikeshaw on 2005-12-12
OK... it's my first Linux install and I guess I shouldn't be surprised there would be a problem.  From reading other posts, I take it my display settings are not correct, so Ubuntu can't boot into Gnome or KDE.  Here's what happened and maybe someone can help.

I installed Ubuntu on the second half of my hard drive (Windows 98 lives on the other)  Grub works great and the dual boot is all good.  The problem is when I try to boot into Ubuntu, I get a curser that eventually stops blinking.  The only way I know to get out of that is hit reset on my computer.  (Actually unplug it, it's an HP Pavilion 8665c and there is no reset button!).  Another post directed someone else to run sudo dpkg-reconfigure xserver-xorg.  It asks a series of hard questions about my hardware.  I've managed to get a lengthy error message that makes no sense, but that's better (I guess) than a blank screen with a curser in the upper left hand corner.

Here's my question (finally).  How do I find out about my hardware?  If memory serves, I have an ATI All-In-Wonder Pro, but I don't know which slot I plugged it into or what it's address is, much less all those questions about my monitor, etc.  Is there an easier way to do this????

Thanx for any help that might :cool:

---

### Post by localzuk on 2005-12-12
I would suggest that you dig out the manual that came with your monitor/bits of hardware and/or look at the manufacturers website and/or look on the bits of hardware themselves (open the case of the tower but not the monitor).

---

### Post by mikeshaw on 2005-12-12
That's OK... I'm doing the best research I can.  Not knowing anything is frustrating.  For instance, while I'm going through the **sudo dpkg-reconfigure xserver-xorg** menus, I don't know how to add or remove *'s next to selections I'd like to select or de-select.  I've hit delete, backspace, F1, etc., etc.  Enter just moved me to the next menu page.  Frustrating.  

Also, how do I figure out the PCI address of my ATI All-In-Wonder Pro with 4 MB of RAM?  The IRC Channel in Windows is 11, does that mean anything?  All of this seems very hard because not only do I not have the answers, I'm not sure I understand the questions!  That's OK, I'm plodding along and I may or may not figure it out.  I'm just glad my Windows 98 is working great and I haven't lost anything by experimenting with Ubuntu!

Thanx again for any wisdom y'all can impart.

---

### Post by DiscoKiller on 2005-12-12
arrows to navigate, space to select.....i think

---

### Post by mikeshaw on 2005-12-12
Space Bar Worked!  Thank you, that's some sort of progress.  :D 

Still having issues with the other issues.  Here's more info.  In **sudo dpkg-reconfigure xserver-xorg** it auto detects an Intel Chip for my video card.  I believe that is on my motherboard.  When I bought my HP Pavilion 8665c, Pentium III 600 so many years ago, I also bought an ATI All-In-Wonder Pro which I promptly added to an open slot in my computer.  sudo is recognizing the Intel and I want to use the ATI.  I manually enter the ATI info, but I have no idea on the PCI Address, nor do I have any idea where to find that info.  I left it blank and that didn't work either.  Part of the error message is: "Failed to open frame buffer device."  

I feel like I'm close, and yet, I remain clueless :???:

---

### Post by ddtmsa on 2005-12-13
[QUOTE=mikeshaw]  In **sudo dpkg-reconfigure xserver-xorg** it auto detects an Intel Chip for my video card.  I believe that is on my motherboard.  When I bought my HP Pavilion 8665c, Pentium III 600 so many years ago, I also bought an ATI All-In-Wonder Pro which I promptly added to an open slot in my computer.  sudo is recognizing the Intel and I want to use the ATI.  I manually enter the ATI info, but I have no idea on the PCI Address, nor do I have any idea where to find that info.  I left it blank and that didn't work either.  Part of the error message is: "Failed to open frame buffer device."  
[/QUOTE]

The PCI Address and other information can be found in your W****w's  System settings in the Control Panel, look under Harware -> Device Manager -> Display Adapters. I installed a PCI nvidia card and had to manually reconfigure my settings using the **sudo dpkg-reconfigure xserver-xorg** command. In my case the PCI address was 1:0:0 for the nvidia card while the onboard intel graphics was 0:2:0

---

### Post by mikeshaw on 2005-12-13
Thanx for the help.  Unfortunately, that's where I've been looking, but the PCI Address is nowhere to be found.  Maybe because I'm running W****ws 98?  (too funny with the *'s!)

I've been reading in the sound/display threads about **sudo apt-get install gatos**, but that didn't work either.  It kinda reminds me of the first hard drive I installed.  It was a weekend of frustration because it was all new to me.  Now I can add a hard drive in my sleep!  I'll figure this out too (with lots of help from all y'all, no doubt), I'm just anxious to get going!

---

### Post by mikeshaw on 2005-12-13
SUCCESS!!!!

Turns out I was right about the PCI Address being 1:11:0, but the format had to be 01:11:0.  Then I was getting an error on the monitor.  I had to go to "advanced" and accept the default on ranges for monitor size and refresh rate.  I was using "medium" and chosing 1024x768 at 60Hz (which should've worked, but didn't).  Anyway, I'M IN!  I'm writing this right now from Mozilla Firefox in Ubuntu Linux!  Too bad I have to be at work in an hour.  I want to explore!  :D 

Thanx for all your help!

---

