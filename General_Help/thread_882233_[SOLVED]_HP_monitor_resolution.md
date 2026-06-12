---
title: "[SOLVED] HP monitor resolution"
date: 2008-08-06
forum: General Help
---

### Post by si.young on 2008-08-06
Hi,

I have just installed a new Nvidia 8600gt card into my Hardy PC and enabled the restricted nvidia drivers. Now the card seems to be working OK but the Monitor is not being recognised (its just an 17" HP)and the screen resolution is way too low with no option to raise it. If I disable the driver, the monitor is recognised as an HP, but the res is even worse. What have I done wrong.

Thanks

Another nOOb Linux user...

---

### Post by nbayiha on 2008-08-06
You will need to edit you xorg.conf file.
Just go to the **_Part IV number 8 9 and 10_** of this thread [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) and i think that will fix your problem

---

### Post by jonian_g on 2008-08-06
Open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that comes up look if your monitor model is next to "Model:". If its not, click on it and find it in the list.
If its not in the list, instert in the drive the disc that came with your monitor, click "add" and locate the .inf file in the disc. If you don't have the disc choose a generic model with the maximum res your monitor can handle (probably 1280x1024).

I would recommend also to install the latest nvidia drivers with envy, as they have improvements for geforce 8 series.

To install envy, open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System>EnvyNG and install the drivers.

---

### Post by jonian_g on 2008-08-06
> **nbayiha said:**
> You will need to edit you xorg.conf file.
Just go to the **_Part IV number 8 9 and 10_** of this thread [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) and i think that will fix your problem

Nice and complete how to but no need to edit you xorg.conf manually.

---

### Post by si.young on 2008-08-06
Thanks for the help guys, appreciate it. I will give this a go.

---

### Post by nbayiha on 2008-08-06
first try what @jonian_g said , cause it seems to me that it's much more accurate, if you don't succeed with it them try my way . And don't forget to mark thread as solved (>>thread tools<<)if you get resolve your problem.:)

---

### Post by si.young on 2008-08-06
Will do, I am not home right now so I will have to try it after work. How do I leave thanks.

---

### Post by si.young on 2008-08-07
Thanks guys all fixed:)

---

