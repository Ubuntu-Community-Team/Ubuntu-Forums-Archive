---
title: "laptops cant hybernate when using opengl?"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by pontifex3 on 2007-06-06
hi, i have an hp V6000Z and am thinking of putting feisty in it along with beryl, but i read in a french webpage that ubuntu has the problem that if your laptop is running anything using openGL such as Beryl and you put it to sleep of hybernate, your computer will be unable to revive(or whatever you call it :P ), so each time you want to close your computer without shutting it down, you have to first shut down anything using openGL, does anybody know if this is true or false? because i havent been able to find any other webpage mentioning this, thanks!

btw, does anybody know if the remote control that it comes with works fine under ubuntu? thnks!

---

### Post by benanzo on 2007-06-06
I don't know about the remote, but I can say that sleep/hibernate *do* work with OpenGL running, but it very much depends on what graphics driver is being used.

All the integrated Intel chips have great support.  The Free nvidia (nv) and non-Free (nvidia) and the Free ATI (radeon) modules have good support for sleep/hibernate as well even while OpenGL is running.  I am not sure about the non-Free ATI driver (fglrx).  I seem to remember a lot of discussion about that very problem.

nVidia and Intel chips are safe...ATI is problematic.

---

### Post by hardyn on 2007-06-06
beryl will not work ( i hear there is a work around now) with nvidia.
I have found i must add vga=791 to the grub boot string when using both the ati and nvidia drivers.

---

