---
title: "Fujitsu L7320GW ubuntu 9.04"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Phillip Hutchinson on 2009-10-19
I am new to Ubuntu and love it (I hate Microsoft). But can I get the operating system to work on this laptop, not likely! The main problem and I have tried to get help from previous threads without luck. The Problem is that the Laptop has a widescreen, I can install Ubuntu 9.04 but when you go into the desk top the right hand side of the screen and the bottom of the screen are not visible.
 
I have seen that you can download drivers for the laptop Via CN800 UniChrome Pro but I don't know where to start how to instal it.
 
Please help I'm running out of patience and I may have to return to XP the enemy.
 
Regards
 
Phillip

---

### Post by Mark Phelps on 2009-10-19
Linux is not Windows -- you don't routinely install drivers.  Drivers are installed routinely as part of setup.  If you're seeing a desktop, video drivers have already been installed.

In some cases, there are "restricted" drivers -- but those are only available for specific ATI and Nvidia cards.  There are no such drivers for other cards/chipsets.

What make/model is your video card/chipset?

---

### Post by Phillip Hutchinson on 2009-10-19
UniChrome Pro with 64MB Shared Fujitus Seimens Notebook.
 
Regards
 
Phillip Hutchinson

---

### Post by Mark Phelps on 2009-10-19
Found a couple of different sources that list different video adapters for your machine.  To find out what you have, open a terminal and enter "lspci" -- and look for lines that mention video adapters.  Those are usually near the end of the list.

---

### Post by Phillip Hutchinson on 2009-10-22
Have tried "lspci" but this looks like incorrect information.
 
According to Fujitsu this should be as follws.
 
Display
Display Type: 15.4" TFT
Max Resolution: 1280 x 800 ( WXGA )
Widescreen Display: Yes
Features: Crystal View
Video
Graphics Processor / Vendor: VIA UniChrome Pro
Video Memory: Shared Video Memory (UMA)
Max Allocated RAM Size: 64 MB
 
Regards
 
Phillip

---

