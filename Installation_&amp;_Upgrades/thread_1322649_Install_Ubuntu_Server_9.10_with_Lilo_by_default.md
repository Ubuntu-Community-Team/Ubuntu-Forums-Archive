---
title: "Install Ubuntu Server 9.10 with Lilo by default"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by marquinos on 2009-11-11
Hi! I have an older computer. This computer with Grub not starts.
How can I install Lilo by default in the installation of Ubuntu Server 9.10? (Preferably configuring the start options when LiveCD starts with F6, please).
Thanks in advance :)

---

### Post by atoztoa on 2009-11-11
> **marquinos said:**
> How can I install Lilo by default in the installation of Ubuntu Server 9.10?

You can use the alternate CD to install LILO...

OR

Try [http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html](http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html) ... it may give you ideas...


_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by marquinos on 2009-11-11
Thanks atoztoa for reply ;)
Not exists the alternate for Server edition, and I don't like more menus for choose.
The Ubuntu Server CD come with LILO options in a hide menu (if the instalation crash). I think that with a exact parameter, it must works.

The links works reinstall LILO over GRUB :( I think I will do it, with Super Grub Disk.

---

### Post by marquinos on 2009-11-11
I found the solution :D
When the instalation finish, a dialog appears:
<back>     <continue>
Select Back, and a menu for install LILO or all options in installation appears :D
Cheers!

---

