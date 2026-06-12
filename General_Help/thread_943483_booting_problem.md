---
title: "booting problem"
date: 2008-10-10
forum: General Help
---

### Post by naval pandey on 2008-10-10
hey guys, i m using ubuntu and Win XP in my pc as a dual-boot system.
The problem is that there is some problem in boot-priority of OS. So,
when i am editing menu.lst, it is not getting saved. How can i edit menu.lst

---

### Post by drs305 on 2008-10-10
> **naval pandey said:**
> hey guys, i m using ubuntu and Win XP in my pc as a dual-boot system.
The problem is that there is some problem in boot-priority of OS. So,
when i am editing menu.lst, it is not getting saved. How can i edit menu.lst

You may not be editing it with administrative privileges. Since menu.lst is a system file an ordinary user cannot edit the file. I would recommend a different solution, but to edit it:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.10102008
gksudo gedit /boot/grub/menu.lst

```

The easiest and safest way for inexperienced users to edit menu.lst is with StartUp-Manager (SUM), a gui based app. SUM can set the default OS/kernel, number of kernels to display, how long the menu is displayed until it activates a preselected default, and much more.

To install:
```
sudo aptitude install startupmanager
```

To run:
System, Administration, StartUp-Manager

SUM is easy to use, but I've written an tutorial that will probably answer your questions about how to use it should you have any:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

