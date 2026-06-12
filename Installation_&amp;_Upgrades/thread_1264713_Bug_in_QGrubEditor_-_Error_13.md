---
title: "Bug in QGrubEditor - Error 13"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by maximilion on 2009-09-12
Hi, just installed Xubuntu 8.10.4 32-bit from the LiveCD. After installation I wanted to make my XP 64-bit the default and set the timeout to 2 seconds.

First, I copied the menu.lst file to home/BKP.

I used "Add/Remove" to get QGrubEditor, moved the XP 64-bit entry to the top (thus becoming default), and changed the timeout from 10 to 2 seconds. I then clicked Quit to exit the program, since the Apply button was greyed out and the interface was non-intuitive.

With these simple actions, I now get "Error 13: Invalid or unsupported executable format".


I will restore my backup menu.lst and edit it manually, I think. Could you suggest grub editors that work, or perhaps a Grub replacement (since I think it loads very slowly... GRUB was first installed in 2006 or something with Ubuntu 7.04 64-bit, I think, and has always taken 10-12 seconds, from "Loading GRUB" to "menu appears". Normal??)

---

### Post by maximilion on 2009-09-14
I changed two numbers in menu.lst manually, and it works. If I select Windows from GRUB, another screen appears, where I can choose between Windows XP 64-bit Edition, and "Windows XP (default)". 

This screen wasn't there when I installed XP 64-bit, and the default option results in an error message. I assume GRUB installed it. Which file do I edit (or remove)? 

I don't really need two options and a timeout, since one of the options doesn't work ;)

---

### Post by drs305 on 2009-09-14
As long as you are using Grub 1 (legacy) I'd recommend you become friends with StartUp-Manager. It's a GUI grub editor that allows you to tweak a lot of settings, including timeout, default OS, etc.

Click the "SUM" link in my signature line. The guide explains how to install SUM and details the various options. If you prefer to edit menu.lst manually, there is information on that as well.

I am not sure which "Options" you mean. Windows options or recovery mode/alternate kernel options. SUM doesn't deal with the secondary Windows menu but can control how many kernels you see, whether the recovery mode options are visible, etc in the first boot menu that appears. These are all contained in the /boot/grub/menu.lst file, which is the file SUM tweaks.

---

### Post by maximilion on 2009-09-14
It's a menu that looks a lot like the GRUB menu, which appears after you've selected Windows in GRUB.

Maybe by setting default boot harddisk to hdd(0,0) instead of (0.2) will automagically, you know, boot a default OS directly. (Quickly turns sarcasm off, it's a multiboot machine so I have myself to blame... could be more straightforward tho. Like 'Select windows or linux, and then one of them starts!!')

I did actually ogle the SUM when it appeared next to Kgrub and Qgrub in the package manager... and will now install and try it out and read your linked info. Thx... here's hoping I'll make a nice simple bootmenu without destroying my computer :)

The slow loading should be the old (Sept 2005) BIOS on this old comp struggling with recognizing the ext3 partition... I think. I should actually time the "GRUB loading" sequence, WAY too much time for a menu.

---

