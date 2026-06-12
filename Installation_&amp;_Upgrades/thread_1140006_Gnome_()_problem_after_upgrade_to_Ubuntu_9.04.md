---
title: "Gnome (?) problem after upgrade to Ubuntu 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by hector2000 on 2009-04-27
I just upgraded 8.10 to 9.04 and after a reboot (the grub still says 8.10) I get to the new login screen where I put my credentials. No problem until this point but then when it starts up the Gnome panels and the mouse cursor are blinking constanly and there is no contain in the upper panel. This means, I cannot do anything except Ctrl-Alt-Del. The terminals are working fine so I guess this is going to be some Gnome problem (or x11 maybe?).
Does anyone have a clue why is this happening, and more importantly how can I solve this? It would be really appreciated, thanks.

---

### Post by moze on 2009-04-27
> **hector2000 said:**
> 
Does anyone have a clue why is this happening, and more importantly how can I solve this? It would be really appreciated, thanks.

I had same kind of problems when upgrading my laptop to Jaunty. In my case the problem was a mixup with libgtk-x11-2.0 files and links in /usr/lib directory. I just deleted all the files starting with libgtk-x11-2.0.so.0 from /usr/lib expect libgtk-x11-2.0.so.0.1600.1. Then I created a symbolic link libgtk-x11-2.0.so.0 which points to the file libgtk-x11-2.0.so.0.1600.1 by typing "sudo ln -s /usr/lib/libgtk-x11-2.0.so.0.1600.1 /usr/lib/libgtk-x11-2.0.so.0". 

That solved my problem and everything seems to be okay now. Be carefully if you try that and make sure that you have backups of the libgtk-x11-2.0 files before removing them.

---

### Post by hector2000 on 2009-04-27
Thanks!
Unfortunately I tried to fix it with dkpg-reconfigure -a, and now it crashes before I get to the login screen. The console says that the Nvidia modul long with other moduls fails to start.
Then after like 10 minutes it drops me to the login screen, but no keyboard or mouse input is possible...

---

