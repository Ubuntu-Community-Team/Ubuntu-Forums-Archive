---
title: "Desktop icons not showing !!"
date: 2008-08-22
forum: General Help
---

### Post by syedaliraza on 2008-08-22
hello everybody

I am using Ubuntu which is installed in C: drive along with windowsXP 

now the problem I am facing is that when I open my Partitions from Places menu then each drive has make a shortcut on desktop..but when i restart my ubuntu the icons will be disappear..

please help me how to make hard disk shortcuts on desktop which can not disappear automatically..

Thanx

---

### Post by Alaric on 2008-08-22
Try running this:

gksu gconf-editor <enter>

then go to apps > nautilus > desktop and check the "Computer Icon Visible" box.  This will create a windows-like My computer icon on your desktop.  I, for one, prefer it to listing all of the drives on the desktop.  Good luck :)

---

### Post by alxlabs on 2008-08-22
Probably those partitions are not mounted permanently at startup. You need to add them to /etc/fstab, so run "sudo gedit /etc/fstab"
Google for fstab syntax.

---

