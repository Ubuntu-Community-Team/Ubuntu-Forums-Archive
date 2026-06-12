---
title: "Breezy Mouse Problems - Unresponsive UI to mouse"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Velox Letum on 2005-10-13
Okay, so, I'm still running Breezy Preview...am planning to update when I return from work, however I wonder what the differences between the update two nights ago and final will be. Anyways, I installed Kubuntu Breezy from the CD onto a separate partition in order to experiment and check that it worked well with all of my hardware, however it didn't. 

My mouse, while it works and moves around the screen, will not interact with the UI. At first it does, then less than a minute after boot it stops, and sometimes starts working correctly. I can't hover over icons, click them, click form elements, or anything, though when I had a Konsole screen open I was able to select between two tabs with my mouse, even though I couldn't interact with anything else. Sometimes the mouse started working correctly though. This occurs both on GNOME and KDE, though I found that my mouse had the best possibility of starting to completely work on GNOME. 

My mouse works correctly on [K]ubuntu Hoary, so it seems the problem lies in Breezy. I also tried a PS/2 mouse, but it did not seem to help. *dmesg* revealed no information into the problems. Any ideas?

Kubuntu/Ubuntu 5.10 Breezy Preview (updated Oct. 11)
Intel Pentium 4 3.00GHz HTT
Intel Bonanza D875PBZ (Mainboard)
Intel Canterwood i875P (Chipset)
1GB Coursair PC3200 DDR SDRAM
Default Kernel (2.6.12-8-386, tried compiling 2.6.12 kernel...686, no difference)
Microsoft Intellipoint USB Mouse

---

### Post by John.Michael.Kane on 2005-10-13
There are issues with touchpads in 5.10 sorry. as of now i know of no work around.

---

### Post by Velox Letum on 2005-10-13
The thing is, it isn't a touchpad. Its a USB mouse. The same problems occur with a PS/2 mouse. A conventional mouse.

---

### Post by tseliot on 2005-10-14
[QUOTE=Velox Letum]The thing is, it isn't a touchpad. Its a USB mouse. The same problems occur with a PS/2 mouse. A conventional mouse.[/QUOTE]
Open Ksysguard and look at the CPU usage.If it is 100% (or high) then see which application can be causing your problem

---

### Post by Velox Letum on 2005-10-16
It isn't a program...and the mouse input is constant. I checked it by running cat /dev/input/mice...it works, though it seems some bit of code in Breezy thats different from Hoary prevents it from consistantly working with the UI. Earlier I tried upgrading...no dice. I could switch windows by right clicking on the taskbar element then clicking it, but after an xorg reboot that didn't work...its very inconsistant, changing from reboot to reboot.

---

### Post by zapik on 2006-11-21
I have a similar problem.  In my case the mouse works either on the screen or the menus, but not in both.  Right now I am typing in Firefox, and this is what is happening:
- If I switch tabs with Ctr+tab, the menus work, until I click on something on the screen.  Sometimes it allows me to click, sometimes not.
- If I manage to get it working on the screen, then it doesn't work on the menus.  This is consistent.
I just wanted to add more information, the solution I am going to take is installing a previous version of Ubuntu, this may be too much for this computer.
The version is Ubuntu 6.10, on an old Dell box (Optiplex GX 150)

---

### Post by kdevoll on 2006-11-24
I have the same problem on:
Ubuntu 6.10
HP P3 600Mhz
ATI Rage AGP graphics

I can mouse the mouse but get no response to clicks.

Kevin

---

### Post by Nush_W on 2006-11-25
I had a similar problem, albeit using a Bluetooth keyboard and mouse.

I found turning **F Lock off** restored the mouse's functionality.

Give it a try...

---

