---
title: "ATI Radeon Display Problems"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by 1337_ubunutu_teen on 2007-09-10
:confused:I have an HP Compaq 6715b laptop.  I cannot get x.org to detect my display.  I am running an AMD Turion 64 X2 Mobile TL-52 (1600 MHz),  with integrated ATI Radeon x1250.  I think I have found the Linux drivers, but I do not know how to install them from a cd in the command terminal (because my GUI will not boot) Please help!!!!!!!!!:(

---

### Post by eggdeng on 2007-09-10
At the prompt, type ```
sudo nano /etc/X11/xorg.conf 
``` Find  the section Device, it will contain a line like ```
Driver      "ati"
``` Change ati or whatever it is you find to vesa. Press Ctrl+x, Shift +Y to save and then Intro. What you have done is tell xorg to use the generic vesa driver instead of the bundled ati driver. This should allow you to reboot into a GUI so you can start working on the driver. I would be very wary about installing anything off a CD. As far as I know, there is an option in the system menu in Feisty to enable restricted drivers.

---

