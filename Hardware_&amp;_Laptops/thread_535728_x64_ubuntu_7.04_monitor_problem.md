---
title: "x64 ubuntu 7.04 monitor problem"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by pwnage101 on 2007-08-26
thought i should move this question over to the people that know about the OS i'm having problems with:)


[my build]("http://forums.steampowered.com/forums/showthread.php?t=590917")
q6600
4gb (4x 1gb) crucial ballistix DDR2 800
8800gtx
gigabyte GA-P35-DS3R

old 1024x768 CRT
new 1680x1050 LCD

here's what I said at Steampowered:
> **pwnage101 said:**
> so i installed linux on this native 1024x768 CRT and its all good. i brought the comptuer back upstairs and hooked it to my new 1680x1050 LCD. i get gigabyte logo....checking GRUB....loading linux and i get a blank screen. it never goes on....just black. i pressed the power button and it gave a beep and turned off ten seconds later as if linux was "unloading" (or whatever it usually does). it was as if the monitor just refused to show me the OS. i hooked it up to the crt and it was fine. i got the gui on the screen...no problem. i hooked it back up to the lcd and loading linux....blank.

perhaps there's a problem with resolution settings? i tried to boot from the linux installation disk and the exact same thing happens. everything is ok with CRT but poop with LCD.

should i format and install linux with the LCD?

---

### Post by ankorie on 2007-08-26
Your problem might lie in your /etc/X11/xorg.conf file under the "Monitors" and "Screens" section, but it also sounds like you are not even getting that far. I am unfamiliar with GRUB so I am no help there I do know that LILO sets your console screen size and depth when you boot. Mabe someone who knows more about GRUB can post some more info. 
Good luck
Ank

---

### Post by pwnage101 on 2007-08-27
> **ankorie said:**
> Your problem might lie in your /etc/X11/xorg.conf file under the "Monitors" and "Screens" section, but it also sounds like you are not even getting that far. I am unfamiliar with GRUB so I am no help there I do know that LILO sets your console screen size and depth when you boot. Mabe someone who knows more about GRUB can post some more info. 
Good luck
Ank

but the live CD is all temporary stuff stored in the ram. and when i try to boot into the liveCD through the widescreen, i get the menu....30 second countdown.....hit enter on the first option....loading linux kernal....blank
The only way i could install linux is through the CRT. like i said, it's as if the LCD just takes a curtain and covers the GUI of ubuntu...

---

### Post by ankorie on 2007-08-29
oops I'm sorry I did'nt read all of your post apperently because I did not know you are useing the live cd. Have you tried to use the safe graffics mode on the installer?

---

