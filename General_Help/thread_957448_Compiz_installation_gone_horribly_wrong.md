---
title: "Compiz installation gone horribly wrong"
date: 2008-10-24
forum: General Help
---

### Post by gilaniali on 2008-10-24
I was trying to install Compiz on my Dell Inspiron 6400 laptop which has an ATI card and 15.4" screen and runs XP and Ubuntu in dual boot, and followed the steps i found online. But after reboot, my resolution is completed messed up. Everything is too big. I cant change the resolution which is now stuck at 800*600.

I do not have data on linux yet, so can i simply reset the entire installation? or is there a quicker way to fix this?

---

### Post by MaxIBoy on 2008-10-24
If you don't have anything on it yet, go ahead and use a full reinstall, then use [fusionbuild](http://ubuntuforums.org/showthread.php?t=871165) to get Compiz.

---

### Post by gilaniali on 2008-10-24
and how do i do a full reinstall? Will that take out my XP partition and the data on it? Isnt there a reset button in the OS?  

Ag

---

### Post by blackened on 2008-10-24
Would probably be easier to just reconfigure the xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

Accept the defalts, then

```
sudo /etc/init.d/gdm restart
```

---

### Post by MaxIBoy on 2008-10-24
Didn't know how to do that reconfigurement. I be that'll save me a lot of trouble someday. :)

---

### Post by gilaniali on 2008-10-24
Thanks blackened. That fixed it!

Now if I can only get my Wifi to work I'll be set to go. I have posted in the Wifi section no replies yet. Care to take a look?

[http://ubuntuforums.org/showthread.php?t=957440](http://ubuntuforums.org/showthread.php?t=957440)

---

