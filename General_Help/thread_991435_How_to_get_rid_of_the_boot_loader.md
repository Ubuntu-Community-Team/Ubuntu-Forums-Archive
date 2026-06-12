---
title: "How to get rid of the boot loader?"
date: 2008-11-23
forum: General Help
---

### Post by ndefontenay on 2008-11-23
Good morning,

I've completely switched to Ubuntu recently after removing the remains of what was left from windows but I still have it in my boot list from when I was dual booting.

I've search on the forum existing thread without much success.

It would be great if someone could tell me where to get the grub configuration file.

What I would like to get is no choice at all when I startup. I just want Linux to start like it would be on windows.

thanks in advance,

Nico

---

### Post by jimmy the saint on 2008-11-23
[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

a great primer on grub

---

### Post by TeXtonyx on 2008-11-23
gksudo gedit /boot/grub/menu.lst 

edit and delete the section of menu.lst 
named 'other operating system' (it comes after the Ubuntu entries)
that refers to your prior Windows installation.
Save

---

### Post by ndefontenay on 2008-11-23
Thanks a bunch guys.

The link for the splash screen is pretty great too!
I'll be looking into this for greater booting experience : )

Nico

---

