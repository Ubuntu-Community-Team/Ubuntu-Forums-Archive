---
title: "unable to open any programs (freeze)"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ceci123 on 2009-01-10
Please help... this is my work desktop. 

I am using Ubuntu 8.1 hardy on a dell desktop. I really don't know what caused this problem.... but this is what happened. 

I had a lots of updates that needed to be done. So clicked the update icon and happily when and updated... and flashed me (something about **"/var/cache/apt/archives/acrobatad_8.0.2-i386.deb: trying to everwrite '/usr/bin/acroread', ** which is also a package...").  I DON"T KNOW IF THIS CAUSED THE ERROR but 

after a reboot  i could not open any programs. It freezes. 

However, I can open all programs if I 
**reboot >> Session >> Failed Safe Terminal >> gnome-panel & **
When i do this I get this msg: "Unable to open desktop file /usr/share/applications/mozilla-thunderbird.desktop for panel launcher: No such file or directory."

But  I can open Firefox and other programs but as soon as I exit everything is frozen again. 

How can I fix my problem?! Please help. 

Thank you for your help.

---

### Post by ceci123 on 2009-01-11
nobody?

i am still having the same problem. if i try re-installing the OS....will it wipe all the contents that i currently have on my machine?

help. 

thanks

---

### Post by avtolle on 2009-01-11
Try from the terminal (Applications-->Accessories-->Terminal)```
sudo dpkg --configure -a
``` to see if that cleans up the problem.

---

### Post by ceci123 on 2009-01-11
Hi there. 

Thanks for taking the time to help me out. 

I issued the command you suggested and it didn't return anything. It just returned to the  prompt. The complete system is frozen! 

By pressing** 'Esc' button I can boot to my previous version eg. Ubuntu 8.04.1, Kernel 2.6.24-16-generic. ** But the resolution is all messed up.

What can I do? 

thanks

---

