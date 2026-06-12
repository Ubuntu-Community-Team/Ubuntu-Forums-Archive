---
title: "How do i use a .run file...???"
date: 2008-11-01
forum: General Help
---

### Post by jbpbgame on 2008-11-01
I want to install a driver for may video card...
"RIVA TNT2 Model 64/Model 64 Pro" is my video card..

I downloaded a file from the site of nvidia... the filename of this file is "NVIDIA-Linux-x86-71.86.06-pkg1.run"

the problem is i just recently started using Ubuntu... and I dont know what to do with it...(actually Im really a beginner here in linux world..) 
I hope someone out there can help me... hehe..

---

### Post by RATM_Owns on 2008-11-01
Press ALT+F1 (you may have to hold it down)

Log in, type ```
sudo /etc/init.d/gdm stop
``` then run ```
sudo sh NVIDIA*.run
```

Then restart.

Or you could use envy.
```
sudo aptitude install envyng-core envyng-gtk envyng-qt
```

---

