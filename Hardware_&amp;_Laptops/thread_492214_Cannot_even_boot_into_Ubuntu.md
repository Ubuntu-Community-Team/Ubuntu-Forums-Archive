---
title: "Cannot even boot into Ubuntu"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by Gndoab on 2007-07-04
Hi, I have a brand spanking new (3 days old at this point) HP laptop (the HP Pavillion dv9428nr...specs at the bottom of post). I figured I'd try installing ubuntu, mainly because vista is a bloated resource wh*re. The first problem arose when I tried to run the live CD. It will not start unless I booted it into safe mode. The screen just stays black, although it is illuminated as if it were showing something (thats the best I can describe it). So I figure no big deal, Ill just boot the live cd safemode. 
All is good and it installed, but now that it is installed, i cannot run the OS w/o having the same problem. I can't even boot into the OS. I tried to run it in safe mode, but that brings me to a command prompt, and I have no idea what to input. I don't even know where to start.

If this can be solved, then I think I can try and figure out why I cannot connect to any networks.

HP pavillion dv9428nr PC
17' monitor
Geforce go 6150 (this card is kind of old, so I don't know why ubuntu has such a problem with it)
AMD Turion 62X2 (2.20 GHZ)
2048 MB ram
125X2 GB HD
Conexant HD Audio 

Also, and I dont know if this helps at all, when I boot into the Live CD from safe mode (whatever the linux equivalent is called), I do not have the option in the resolution panel to change the resolution to a widescreen aspect ratio. So yeah, let me know if there is anything else I need to add to this, and any help is appreciated.

---

### Post by Gndoab on 2007-07-05
Does anyone have any idea's on what to do?

---

### Post by Swankyman on 2007-07-05
Hi

Hummm.

reading this thread looks like similar problem

[http://ubuntuforums.org/showthread.php?t=490372&highlight=Geforce+go+6150](http://ubuntuforums.org/showthread.php?t=490372&highlight=Geforce+go+6150)

looks like a bug with the 64bit version. you can install the 32bit to get rid of it!!!!

if you need help with that just ask :D

rich

---

### Post by Gndoab on 2007-07-05
thanks for the reply

I don't have the 64 bit version of ubuntu, I have the 32 bit (thanks for the suggestion though)


Something new, I recently installed WMware on my PC (on vista), and setup a WM using the SAME cd I used to do a fresh install, and everything works perfectly. It installs fine, I have an internet connection (something I have never been able to achieve in linux before now), and the display does not go to black (in fact I can even run it in 1440*900 widescreen).

Why would it work perfectly as a WM but not as a regular install? anyone know?

---

### Post by jonathanmotes on 2007-07-13
I have the exact same laptop you have. I just got it last week and have made some progress. I have so far gotten Ubuntu installed with Vista and have the correct resolution. I have GRUB so that I can select what operating system to boot. I am still working on getting the wireless to work though. Here's what I've done:

I had to use the alternate install disk. (also available from Ubuntu.com). (With this disc, you will have to install Ubuntu before booting the desktop.)

I have Vista on my laptop, so I used this tutorial:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) 
to shrink the vista partition. (I wanted to use my second hard drive to store files that I could access from either Vista or Ubuntu.)

When I first booted into Ubuntu after installing, the resolution was at 1280X800 and that was also the highest resolution I could select. I decided to try to install the nVidia driver and see what happened. When I rebooted, the correct resolution of 1440X900 pixels was already enabled. I think the easiest way to install it is to select the System dropdown > Administration > Restricted Drivers Manager. I wanted the desktop effects, so I went to System > Preferences > Desktop Effects and selected to enable them. The nVidia driver was enabled automatically. If you don't want the nVidia driver, you can also edit the xorg.conf file, but I really don't know how to do it. I have seen a lot of tutorials on doing it that you could probably easily find.

Hope this helps!

---

### Post by jonathanmotes on 2007-07-19
Hey, if you still need help with your laptop, I've figured out how to get most of everything to work pretty well. Just post back here, I will check back here every now and then.

---

