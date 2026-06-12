---
title: "My computer had a stroke"
date: 2008-08-06
forum: General Help
---

### Post by weweboom on 2008-08-06
I used a program to change my login screen, but i screwed it up and now after the boot screen, the screen turns orange, and the cursor just keeps spinning, without logging in. is there some way to bypass the login screen and just login so I can fix what I broke? Is there a system restore type thing like on vista? or maybe just a way to restore a working login screen

---

### Post by cdtech on 2008-08-06
During the grub boot menu select recovery mode option. This will take you to a login prompt.

**P.S.**
Once loged in you can just "sudo apt-get --purge remove whateverprogram" the program you installed that is causing the problem.

---

### Post by weweboom on 2008-08-06
thanks, i know but I don't want to log in in a terminal like app I need to be able to bypass my broken login screen and be able to login to my actual working computer and be able to fix what I broke

---

### Post by cdtech on 2008-08-06
> **weweboom said:**
> thanks, i know but I don't want to log in in a terminal like app I need to be able to bypass my broken login screen and be able to login to my actual working computer and be able to fix what I broke

I did an update on my post. Once loged in, via the terminal, you can remove or fix the problem at hand then reboot into the normal GUI mode.

---

### Post by tuxxy on 2008-08-06
Or once your logged in from terminal you could try and start the gui again by entering this command

```
startx
```

The you could change it back or bypass the screen altogether like in this guide

[http://blog.mypapit.net/2006/11/howto-bypass-ubuntu-login-screen.html](http://blog.mypapit.net/2006/11/howto-bypass-ubuntu-login-screen.html)

---

### Post by weweboom on 2008-08-06
the problem is I can't remember the programs name
all i know is it was a program in system administration, it's name and it could edit the bootloader, usplash, and login screen

---

### Post by tuxxy on 2008-08-06
system > admin > login window ?

---

### Post by cdtech on 2008-08-06
It was probably "Startup Manager" which changed your "/boot/grub/menu.lst". When you get to the "grub boot screen" press your arrow key down before it boots and hi-light the primary boot option you use. Press the "e" key to edit. Hi-light the line that looks like this:
```
kernel  /vmlinuz-2.6.24-17-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro quiet **splash**
```
Press the "e" key to edit the line. Delete the word "splash" from the kernel line and press the "b" key to boot with the changes.

---

### Post by weweboom on 2008-08-07
when i'm in startx, and I try to open login window, it says that I'm not running the right window manager and doesn't open so I can't change logon screen and I'm back where I was

---

