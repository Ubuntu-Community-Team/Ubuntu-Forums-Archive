---
title: "Some display issues."
date: 2008-11-20
forum: General Help
---

### Post by CursedBlade on 2008-11-20
Hi, I am trying to use ubuntu on my laptop, this is my initial thread...

[http://ubuntuforums.org/showthread.php?p=6218497#post6218497](http://ubuntuforums.org/showthread.php?p=6218497#post6218497)

It details my issues i had with installing.. I used vga=771 to get the alternative install disc to display properly, however, if i use any vga options in the grub menu i only get text based login..

If i use nothing i get a black screen, no screen backlight or anything..

I'm out of ideas so i could do with some help.

Thanks guys.

---

### Post by CursedBlade on 2008-11-21
No suggestions?

---

### Post by CursedBlade on 2008-11-21
No-one at all?

---

### Post by benson444 on 2008-11-22
Hey,

It may boot into the desktop if you configure it to use the vesa graphics driver. The graphics chip on my laptop was a VIA UniChrome jobby too but when I tried to boot into X I got dumped to the command line, with some errors shown about xorg not being able to find any screens to use, rather than a blank screen.

Anyway, boot to the login prompt, log in and edit /etc/X11/xorg.conf

sudo nano /etc/X11/xorg.conf

Linux is case sensitive so make sure you put X11, not x11. Look for a section for your video device/card and change the driver line to

Driver    "vesa"

Press Ctrl+x to exit nano, then y to save file, then just return to save as same file name. When back at prompt enter

startx

If it doesn't work a reboot is worth a go. Hope it works for you.

---

### Post by CursedBlade on 2008-11-24
Seem to be having some issues with that... i dont really see much when i run sudo nan /etc/X11/xorg.conf

Here is some more information...

just above the login prompt on the screen i get the following...

> bogl_init failed: EXPLODE

screen init failed
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/sda5) = dev(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 8.10 ubuntu tty1

This happens when using vga options in the boot commands. Without the vga options i cant even get to the login

---

