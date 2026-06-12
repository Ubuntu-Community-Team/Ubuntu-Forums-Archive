---
title: "Sis 672 laptop - Scrambled boot screen / terminal, low resolution on X, poor 2D."
date: 2010-09-16
forum: Hardware
---

### Post by Repgahroll on 2010-09-16
Hello there.

I have an ECS U40 laptop and it has a Sis 672 chipset, Mirage 3+ vga.

I could install the latest 10.04 Ubuntu, using the VESA driver. However, VESA has very poor performance (even simple flash apps plays slow, like youtube video player).

Now I want to use the native screen resolution (1400x900) and also want to be able to use the terminals directly (tty1, tty2, etc.). Also, even removing the splash from grub boot line, the boot screen is scrambled, just like the terminal (dots quickly appearing on screen). 

The sis driver provided on repos doesn't work, and i've tried to install the "sisimedia" driver, but X crashes and returns "failed to load /usr/lib/xorg/modules/drivers/sisimedia_drv.so".

Is there a way to get it working properly?

Thank you very much.

---

### Post by Repgahroll on 2010-09-17
I can't understand, i can see grub menu, i can see the loading messages, but when the system finishes loading an i should see the text-only login screen (booting on recovery mode), i only see strange strips moving, like if it were out of sync. I've even tried the text-only vga modes on grub booting line parameters, but i can't get the non-graphical output working.

Maybe it has something to do with the vsync, because X is displaying 800x600@61Hz, which is very unusual, but i've tried the param vsync=61 and it doesn't seems to change anything.

I really want to use Linux on this laptop.

Thanks.

---

### Post by Repgahroll on 2010-09-17
Okay. Solved the garbled cli problem. The solution was to simply blacklist the vga16fb module. (don't forget to update initramfs).

Now I can use cli to configure X.

---

