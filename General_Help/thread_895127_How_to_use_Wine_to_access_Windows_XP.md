---
title: "How to use Wine to access Windows XP?"
date: 2008-08-19
forum: General Help
---

### Post by TreadLight on 2008-08-19
How do I get Wine (I have installed it and everything) to access my Windows XP Home Edition partition? I want to be able to use mIRC and Flash CS3 Professional.

---

### Post by Naatan on 2008-08-19
Wine is a tool to run Windows applications, it's not for mounting ntfs partitions.

With a fresh Ubuntu 8.04 installation the Windows partition(s) should be automatically added to your shortcuts when you press Places, normally it will simply be called "Windows" and you can just click it to mount it.

If this doesn't work for you, try following the steps here;

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by unca.paka on 2008-08-19
Unfortunately, none of the CS3 apps run under wine, youll have to boot to windows to use em. I've gotten Photoshop CS3 to install, but not able to run. And as far as mirc goes, try one of the alternatives, I use x-chat personally.

---

### Post by cariboo on 2008-08-19
You will have to install your windows aaplications using wine to get them to work.

Jim

---

### Post by TreadLight on 2008-08-19
How do I do that?

---

### Post by rossjman1 on 2008-08-19
Can VMWare or VirtualBox load Windows off a different partition?

---

### Post by Mgiacchetti on 2008-08-19
> **TreadLight said:**
> How do I do that?
Right click open with wine?  once its installed, you go to the wine menu in the applications menu.

---

### Post by unca.paka on 2008-08-19
> Can VMWare or VirtualBox load Windows off a different partition?
Heres a tutorial for installing XP in VirtualBox
[http://ubuntuforums.org/showthread.php?t=769883]("http://ubuntuforums.org/showthread.php?t=769883") 
If you want to do any graphics editing/gaming, your gonna need a mean rig. Think Crysis.

As for installing windows apps using wine,
check out [http://winehq.com]("http://winehq.org") 
Theres an App database that currently shows whats working and how well its working under wine. As well as how-to's

---

### Post by rossjman1 on 2008-08-19
Direct3D doesn't work in virtualbox, but if you have a decently powered computer, you can still do some gaming (I play SimCity 4, for instance). To get good performance you can load VirtualBox with no window manager or anything else running, and it's like running a regular XP install!

---

