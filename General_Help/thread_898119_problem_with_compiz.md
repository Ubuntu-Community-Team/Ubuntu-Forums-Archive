---
title: "problem with compiz"
date: 2008-08-22
forum: General Help
---

### Post by WinterMadness on 2008-08-22
i dont know how to get it to work in kubuntu :\ i used gnome and it works.

what im trying to do is change the title bars via emerald and i cant get it to work anymore. what do i need to do.

---

### Post by eightmillion on 2008-08-22
Try inputing this into a terminal and see what happens. 
> nohup emerald --replace &
Does emerald take over?

---

### Post by eightmillion on 2008-08-22
After that you should open up Compiz Config Settings Manager: **Settings>CCSM** on your kmenu. If it's not there, you can install it with:
> sudo apt-get install compizconfig-settings-manager
Then make sure that the **Window Decorations** plugin is checked and you should be good to go.

---

### Post by overdrank on 2008-08-22
Moved :)

---

### Post by WinterMadness on 2008-08-23
tried all of those and some others and got nothing look:


```

ghost@laptop:~$ nohup emerald --replace &  
[1] 14973
ghost@laptop:~$ nohup: ignoring input and appending output to `nohup.out'

ghost@laptop:~$ 
ghost@laptop:~$ sudo apt-get install compizconfig-settings-manager 
[sudo] password for ghost: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
compizconfig-settings-manager set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ghost@laptop:~$ emerald --replace
Reloading...
Reloading...
Reloading...


```

i also have gnome. but im trying to get all these things to work for kde

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > glxinfo

---

