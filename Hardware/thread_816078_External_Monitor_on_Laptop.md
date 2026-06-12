---
title: "External Monitor on Laptop"
date: 2008-06-02
forum: Hardware
---

### Post by Euphorion on 2008-06-02
I have installed Ubuntu Hardy 8.04 on a elderly Fujitsu Amilo Laptop having a SIS M650 (Rev 00) graphics chip.

The Laptop is connected to an external LCD Screen which is capable of displaying 1280 x 1024 pixels. The LCD Panel in the Laptop can only display 1024x768.

In Ubuntu the Desktop is mirrored on both screens in the resolution 1024x768. Switching the display with the Laptop Keys has no effect. I would like to switch off the LCD Screen and display Ubuntu on the external monitor in 1280x1024. What do I need to do in order to achieve this? The Resolution Settings in Preferences ends at 1024x768, there are no options available a la Windows in which I can set up 2 Monitors.

I have searched this Forum and the User Documentation in Community and have found various very complex instructions, but non which directly apply to this chip and inspire me as a beginner to Ubuntu (since 4 weeks) to make the changes with confidence. Is there by chance a utility available like ATIs Catalyst Control Centre. My second Laptop (Fujitsu Xi-2550) has an ATI Card and the Catalyst Control Centre allows for easy setting up of 2 Monitors.

---

### Post by bigjack on 2008-06-02
With an IBM Thinkpad T-40, in System->Preferences->Power Management I selected the AC Power tab and selected "Do nothing" for when laptop lid closed.  It works for this system.  The laptop screen turns off anyway when closed under these conditions and the external monitor stays on.  Hope it works for your Fujitsu Amilo.

---

### Post by Euphorion on 2008-06-03
Thank you for your reply, closing the lid on the laptop switches off the lid LCD and the external monitor remains on, that is not the problem that I have. My problem is the following:

The LCD in the Laptop Lid has a max resolution of 1024x768. My external Monitor can resolve 1280x1024, the built in Video Chip (SIS M650) supports 1280x1024.

Hence it is my wish to have the Ubuntu desktop on the larger monitor (the monitor is bigger and I see more).

But the limiting factor in the resolution settings in Ubuntu is the LCD in the laptop lid. If I could somehow tell Ubuntu to switch off the LCD in the Lid and use the external monitor only for the desktop and let me set the resolution to 1280x1024.

This Laptop had prior to Ubuntu Windows XP and it was possible in Windows to do what I want to do in Ubuntu. In Windows I could use the Lid LCD and external monitor to extend the desktop over both monitors and use 2 different resolutions 1024x768 for the left monitor and 1280x1024 for the right hand monitor.

---

### Post by drahst on 2009-09-15
has this ever been answered? I'm trying to do something similar... I can't get the laptop to switch displays when the lid's closed to my external. I don't mind using both when the lid's open, I just want to use the CRT when I close the lid. My version is 9.04.

---

### Post by Euphorion on 2009-09-17
Hallo drahst

No this has never been answered but I have solved the problem myself. After having gained more and more experience with Ubuntu and especially with the Terminal and Comand line commands as well as the editing of X-Org setup files I managed to solve my Problem.

With my old Amilo with SIS Chips, I eventually found SIS drivers on [html]http://www.winischhofer.net/mymain/welcome[/html] after studying his instructions very very carefully I managed to get my laptop setup for two Monitors, one being the LCD of the laptop and the other an external monitor.

With my other laptop which is far more modern and has a modern ATI (AMD) Radeon Graphics chip, I managed to achieve the same using the ATI Fglrx driver in conjunction with the ATI Catalyst Setup utility.

Currently in Ubuntu it now seems to be no great problem to setup modern ATI or Nvidia Graphics to use 2 monitors. The only thing here, with the appearance of Jaunty the new ATI propriety driver does not support some of the older Graphics Cards/chips. Therefore if you have ATI Graphics check on the compatibility before moving to Jaunty. 

I hope that this will be of some help

---

### Post by Infoteksec on 2009-10-06
Hi. I'm having similar issues with my aging DELL D400. I managed to set up my TV as an external monitor with 1360*768 just fine on my Acer Aspire One 1024*600 but failed when I wanted to use my DELL with MythTV.

All my DELL can deliver to the external VGA is the laptop LCD resolution 1024*768 though I know the 855GM chipset can do better.

Peter

---

