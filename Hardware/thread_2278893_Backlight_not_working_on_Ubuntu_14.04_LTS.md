---
title: "Backlight not working on Ubuntu 14.04 LTS"
date: 2015-05-19
forum: Hardware
---

### Post by Victor_Santos_Brit on 2015-05-19
Hi, 
Im new here, so i'm sorry for any mistake that i make in this post :-|
So, here is the deal: I have a Samsung notebook and my backlight is always on maximum, except when i put it on minimum. In this case, everything goes black and it's almost impossible to see anything.
I already tried everything that i could find on web. Already edited the file /etc/rc.local. Already tried to change manually the brightness file on acpi_video fold. Already edited GRUB's line. Downloaded samsung-backlight, xbacklight and brightness indicator. Nothing works :(

My FN keys are working and when i change manually the brightness file, it does nothing on my backlight. (but change the file).

My notebook is Samsung 670Z5E-XD1BR. Dual boot (Win8.1 and Ubuntu 14.04.2 LTS)
8 GBs Ram
Intel HD Graphics 4000
AMD Radeon HD 8800M Series

---

### Post by weatherman2 on 2015-05-19
What changes did you make to your /etc/default/grub file?  There are a number of things you could change there, not just one thing, to fix a problem like this.  And you must run "sudo update-grub" whenever you change that file or the changes won't take effect (and then, not til after you reboot).

---

### Post by Victor_Santos_Brit on 2015-05-19
Hi weatherman2, 
I edited GRUB_CMDLINE_LINUX_DEFAULT line, putting at least 4 different combinations :) "
The most recently is GRUB_CMDLINE_LINUX_DEFAULT="quiet splat video.use_native_backlight=1" but i already tried "quiet splat acpi_backlight=vendor" and "quiet splat acpi_backlight=Linux"
Just for example.

---

### Post by Vladlenin5000 on 2015-05-19
Should be "quiet **splash**" and adding parameters is useless if you don't do ```
sudo update-grub
```

---

### Post by Victor_Santos_Brit on 2015-05-20
**UPDATE:**
Never mind, i solved it and i'm back on 14.04 WITH brightness problem haha
Hi Vladlenin500,
I'm pretty sure that was just a typing error, but i'll try it again.
Also, every time i edit GRUB i do update-grub.

**-------------------------**
Hello everyone
I tried to update my ubuntu to 14.10 but it didn't work :( Now, i'm without both (14.04 and 14.10) 
I already format the part of my HD where ubuntu was and tried to re-install 14.04 but now its failling.
Huge bad luck :(
I did everything like the last time i put ubuntu on my machine but when i try to boot in i go to GRUB rescue, where it says that cant find my grub file.
Does anyone knows how do deal with it?
I'm sorry for all this mess, i'm just a newbie trying to get into this world :(

---

### Post by Vladlenin5000 on 2015-05-20
You don't need to format before you reinstall in that scenario. Simply by choosing the / partition an selecting format when at "Something else" the installer do it for you. Just make sure the bottloader - Grub - is being installed to where you want it.

---

### Post by Victor_Santos_Brit on 2015-05-20
Hi Vladlenin5000
I imagine that, but didn't work, so i tried format (didn't work as well). But i manage to get it right. 
Now i'm back where i start.
My brightness still dont work and already checked the splat/splash error.

---

### Post by Victor_Santos_Brit on 2015-05-22
Hello everyone,
I may have found a solution for my problem. 
The comand: 

> xrandr --output LVDS1 --brightness x

Note that LVDS1 may change according to your machine. On the web site where i found it, was LVDS-0
Also, the 'x' there is the value of brightness. Here, its between 0 and 1.

In my opinion, this doesnt quite solve my problem. Its more like jerry-rigged, but it's better than nothing.
I'm still searching for the best solution. One, who really solves it.

---

### Post by snatchell on 2015-05-25
Don't know how relatively new your ATIV is, but upgrading your kernel and bios could help.

---

### Post by Victor_Santos_Brit on 2015-05-27
Hi snatchell,

How do i do this? That's something i never tried before

---

### Post by Vladlenin5000 on 2015-05-27
BIOS is hardware related. You should find the latest BIOS and instructions at the manufacturer's website.
Kernel is the "heart" of an operating system. Without it nothing works. Upgrading means installing a newer version than the one a given release has by default.

---

