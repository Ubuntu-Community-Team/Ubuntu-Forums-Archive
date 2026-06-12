---
title: "&quot;No signal&quot; during boot"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by namespace std on 2008-03-17
My problem is that I cannot see  this boot screen,  because my monitor goes to "no signal" during boot sequence. Is there anything I can do about it ?


[img]http://topi.xdt.hu/images/ubuntu_boot2.jpg[/img]

---

### Post by Existentialist on 2008-03-18
Try changing the resolution of the splash screen to whatever you display is set at.This example would be for a 1024x768 screen resolution. Edit:
/etc/usplash.conf

and add:

xres=1024 (or whatever yours is)
yres=768 (again match your settings)

then run:

sudo update-usplash-theme usplash-theme-ubuntu

If this doesn't work, try it at 1024x768, as that should. If this doesn't work, make sure to check the menu.lst at:

/boot/grub/menu.lst

to make sure that your option for Ubuntu has the parts in bold below:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro **quiet splash**
initrd /boot/initrd.img-2.6.22-14-generic
**quiet**

---

### Post by namespace std on 2008-03-18
> **Existentialist said:**
> Try changing the resolution of the splash screen to whatever you display is set at.This example would be for a 1024x768 screen resolution. Edit:
/etc/usplash.conf

and add:

xres=1024 (or whatever yours is)
yres=768 (again match your settings)

then run:

sudo update-usplash-theme usplash-theme-ubuntu


This worked like a charm! Thanks a lot. :)

---

