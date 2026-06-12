---
title: "[SOLVED] how to move the window space slider 2 enable it to move off the cube"
date: 2008-09-26
forum: General Help
---

### Post by Fertech on 2008-09-26
How do i enable 3d cube in compiz 7.10

Hi,

I'm using compiz, i have the extra plugins, just want to know how to enable the 3d cube, the one where the windows rise off the cube in 3d. this is what i got so far.

fertech@fertech-desktop:~$ sudo apt-get install compiz-fusion-plugins-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-extra is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
fertech@fertech-desktop:~$ 

As you can see i have the newest version
 i read something about, have to move the window space slider 2 enable it to move off the cube.
can someone give me more details.

---

### Post by anotherdisciple on 2008-09-26
You need the settings manager... open a terminal and type this:

```
sudo aptitude install compizconfig-settings-manager
```

After it installs you can change your effects through (System > Preferences > Advanced Desktop Effects Settings).

Enable the cube, rotate cube, and 3d windows. Make sure you have 4 desktops and hit Ctrl + Alt + Left Click to rotate the cube.

---

### Post by Fertech on 2008-09-26
i have 2 horizontal virtual
 2 vertical virtaul
number of desktop is 1 and is gray out, in other words i can't change it
 in the botttom right i see 4 windows
 i have the compiz config setting page but i still did the code,
 this is what i got

fertech@fertech-desktop:~$ sudo aptitude install compizconfig-settings-manager
[sudo] password for fertech: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been kept back:
  firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support 
  rdesktop xulrunner-1.9 xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
fertech@fertech-desktop:~$

---

### Post by anotherdisciple on 2008-09-26
make it:

(4) Horizontal
(1) Vertical
(1) Desktop

---

### Post by Fertech on 2008-09-28
Ok i did what you told me, but still no luck. On the bottom right i have all 4 windows next to each other in a row, is there something else that i'm missing

---

### Post by jerome1232 on 2008-09-28
Did you run the compiz config program and enable the effects.

system->preferences->advanced desktop effects settings

enable 3d cube, rotate cube, 3d windows

---

### Post by Fertech on 2008-09-28
i have the rotate cube. that i can use, it flips the window over to the other side. i can use all other effects. i also have the 3d windows, and the desktop cube.

---

### Post by anotherdisciple on 2008-09-28
> **jerome1232 said:**
> Did you run the compiz config program and enable the effects.

system->preferences->advanced desktop effects settings

enable 3d cube, rotate cube, 3d windows

Yeah.. if you did my first post and second post, everything should be working... 

All you have to do is like I said in the first post...

Hold: Ctrl + Alt + Right Click and use your mouse or touchpad to rotate the cube.

---

### Post by Fertech on 2008-09-28
ok i got it thank you.

---

