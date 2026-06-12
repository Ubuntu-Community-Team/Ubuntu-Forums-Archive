---
title: "Reinstalling Ubuntu grub after xp installation"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Profark on 2009-04-18
i have installed the windows xp and the MBR is overwriten.Ubuntu menu is not showing and computer directly runs form xp.how i will install the grub i had tired the following

1. I insert the Ubuntu cd into the cd rom and select run Ubuntu without any thing to your computer (i mean first option).
2. I open the Terminal and type the following commands

fdisk -l

grub

root (hd0,2)
setup (hd0)

but it gives me error:

Sting Parsing can not done

plz help me thks in advance

---

### Post by Herman on 2009-04-18
The instructions you followed were okay, but they were probably wrtten for all Linux distros. Ubuntu is different from other Linux distros. We have special security in place which requires us to use the word 'sudo' before any command that will make system-wide or important changes.

1. I insert the Ubuntu cd into the cd rom and select run Ubuntu without any thing to your computer (i mean first option).
2. I open the Terminal and type the following commands
```
**sudo** fdisk -l
``````
**sudo** grub
```> root (hd0,2)> setup (hd0)If you open your GRUB shell with 'sudo', you will be asked for your passwoprd, (unless you just typed it in the last few miutes), and you'll be given a shell with 'root' priveleges. (administrator power).
If you forget or don't know you need to use 'sudo', you'll still have a GRUB shell, but it won't be very useful.

EDIT: Also, make sure you type '(hd0)' - as in H D zero, the number zero, - don't type '(HDO) - H D O as in 'O' for orange.

---

### Post by sahabcse on 2009-04-18
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by Keith Hedger on 2009-04-18
Always keep a SuperGrub disk handy, its got me out of similar problems more than once, ( I like to try out different distros, but always come back to Ubuntu ).

---

### Post by king2007 on 2009-04-18
herman, good morning ! can i ask you to help me with my system ? i messed it up completely so i cannot access my windows xp - disc.....:(
:(

---

### Post by meierfra. on 2009-04-18
king2007: Please start your own thread.  In the new thread, include more information. How did you mess up your system?  Post the output of "sudo fdisk -lu".

---

