---
title: "How can I make GRUB look nicer?"
date: 2008-07-31
forum: General Help
---

### Post by Suilenroc on 2008-07-31
So I'm currently dual booting Ubuntu Linux with Windows Vista, and I'm getting annoyed at the rather ugly look of the GRUB boot screen. Is it possible to change it, to look a bit nicer? At least increase the resolution and add a nice background? 

Thanks! -Suilenroc

---

### Post by overdrank on 2008-07-31
> **Suilenroc said:**
> So I'm currently dual booting Ubuntu Linux with Windows Vista, and I'm getting annoyed at the rather ugly look of the GRUB boot screen. Is it possible to change it, to look a bit nicer? At least increase the resolution and add a nice background? 

Thanks! -Suilenroc

Hi and this link has a lot of good info   A LOT :)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by forger on 2008-07-31
Especially take a look at vga defoption, it will allow you to use a better resolution
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

---

### Post by Suilenroc on 2008-07-31
Thanks very much for the info guys!

---

### Post by LowSky on 2008-07-31
there is a application call start-up manager that can help you do everything with the help of a GUI.

---

### Post by monkeyking on 2008-12-11
Theres a package called grub-splashimages
That contains some images you can use as a backdrop in your grub menu.

You still need to update your menu.lst though...

---

